# XPath Articles rules

A collection of xpath rules to extract relevant content from popular websites.


Here's an example about how to use it in PHP:

    <?php
    
    $rules = json_decode(file_get_contents('rules.json'), true)];
    
    $url = 'http://www.theverge.com/2014/8/14/6001153/the-best-fitness-tracker-you-can-buy';
    
    $html = file_get_contents($url);
    
    libxml_use_internal_errors(true);
    
    $doc = new DOMDocument;
    $doc->loadHTML($html);
    
    $xpath = new DOMXPath($doc);
    
    $image = $xpath->query($rules['common']['image])->item(0)->textContent;
    
    $host = parse_uri($url)['host];
    $article_nodes = $xpath->query($rules['hosts'][$host]['content]);
    
    if ($article_nodes->length > 0)
    {        
      $article_node = $article_nodes->item(0);
      $article_text = $article_node->ownerDocument->saveHTML($article_node);
    }
    
et voilà !