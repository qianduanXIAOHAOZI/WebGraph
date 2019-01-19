# WebGraph
This is a crawler similar to Google crawling webpages.

## Algorithm principle
The specific principle of this algorithm is to give an initial web page, then access all the hyperlinks, and then click on the hyperlinks to access the hyperlinks in the web pages it points to, and so on. And based on the number of times the page is linked and the weight of the linked page, the weight of the page is calculated.

## Webpage class
This is a class that stores web page information.
Module: webpage
### Usage
``` python
wp = webpage(url, [weight = 0.001, links = []])
```
#### Create a new object:
``` python
from webpage import webpage
url = "https://www.google.com/"
wp = webpage(url)
```
#### Member function
- url()
TODO: For get the url of this webpage
demo:
``` python
from webpage import webpage
url = "https://www.google.com/"
wp = webpage(url)
print(wp.url()) # https://www.google.com/
```

## weight(links) function
This is a function that can calculate the connected web page based on the linked web page.
Module: webpage
### Usage
``` python
from webpage import webpage, weight
wp1 = webpage("https://www.google.com/")
wp2 = webpage("http://nodejs.org/")
wp3 = webpage("http://www.github.com/")
wp1.links.append(wp2)
wp1.links.append(wp3)
print(weight(wp1.links)) # 0.002
```

## get(pu, url) function
This is a function that can give an initial page and then crawl information continuously.
Global
### Usage
``` python
from webpage import weight, webpage
import urllib2
import re
rcFile = open(".wpgrc")
rc = rcFile.read()
rc = rc.split("\n")
url = "http://yhzheng.com"
get("", url)
rcFile.close()
```

## .wpgrc File
This file can set which fields are not included in the url, and each field is separated by a newline.

## Use sample
```
$: python main.py
The url to be crawled: http://yhzheng.com:30/text/id?id=8
End crawling after a few seconds: 5
Illegal urls: .mod; .css; .js; .png; .jpg; .gif; .jpeg; .ico; .bmp; .dtd; .svg;
Please wait 5 seconds to show the link graph...
 Getting http://yhzheng.com:30/text/id?id=8 ......
Got webpage......
Parsing webpage......
Getting http://yhzheng.com:30/text/id?id=7 ......
Got webpage......
Parsing webpage......
Getting http://yhzheng.com:30/projects ......
Got webpage......
Parsing webpage......
Getting http://yhzheng.com ......
Got webpage......
Parsing webpage......
Found a illegal url, stop access.
Got a found url.
Getting http://yhzheng.com:30/text/id?id=6 ......
Got webpage......
Parsing webpage......
Getting http://yhzheng.com:30/text/id?id=5 ......
Got webpage......
Parsing webpage......
Getting http://yhzheng.com:30/text/id?id=1 ......
Got webpage......
Parsing webpage......
Got a found url.
Got a found url.
Got a found url.
Getting http://yhzheng.com:30/text/id?id=4 ......
Got webpage......
Parsing webpage......
Getting http://yhzheng.com:30/text/id?id=3 ......
Got webpage......
Parsing webpage......
Found a illegal url, stop access.
Got a found url.
Got a found url.
Got a found url.
Getting http://yhzheng.com:30/text/id?id=2 ......
Got webpage......
Parsing webpage......
Found a illegal url, stop access.
Found a illegal url, stop access.
Got a found url.
Please wait 4 seconds to show the link graph...
Please wait 3 seconds to show the link graph...
Please wait 2 seconds to show the link graph...
Please wait 1 seconds to show the link graph...
Please wait 0 seconds to show the link graph...
('http://yhzheng.com:30/text/id?id=8', 1)
('http://yhzheng.com:30/text/id?id=4', 6)
('http://yhzheng.com:30/text/id?id=5', 12)
('http://yhzheng.com:30/text/id?id=6', 2)
('http://yhzheng.com:30/text/id?id=7', 4)
('http://yhzheng.com', 1)
('http://yhzheng.com:30/text/id?id=1', 14)
('http://yhzheng.com:30/text/id?id=2', 1)
('http://yhzheng.com:30/text/id?id=3', 13)
('http://yhzheng.com:30/projects', 1)
[FINISH]
(venv) 192:web-graph zhengyuanhao$ python main.py
The url to be crawled: http://yhzheng.com:30/text/id?id=8
End crawling after a few seconds: 5
Illegal urls: .mod; .css; .js; .png; .jpg; .gif; .jpeg; .ico; .bmp; .dtd; .svg; github.com; baidu.com; google.com; w3.org; imooc.com;
Please wait 5 seconds to show the link graph...
 Getting http://yhzheng.com:30/text/id?id=8 ......
Got webpage......
Parsing webpage......
Getting http://yhzheng.com:30/text/id?id=7 ......
Got webpage......
Parsing webpage......
Getting http://yhzheng.com:30/projects ......
Got webpage......
Parsing webpage......
Getting http://yhzheng.com ......
Got webpage......
Parsing webpage......
Found a illegal url, stop access.
Got a found url.
Getting http://yhzheng.com:30/text/id?id=6 ......
Got webpage......
Parsing webpage......
Getting http://yhzheng.com:30/text/id?id=5 ......
Got webpage......
Parsing webpage......
Getting http://yhzheng.com:30/text/id?id=1 ......
Got webpage......
Parsing webpage......
Got a found url.
Got a found url.
Got a found url.
Getting http://yhzheng.com:30/text/id?id=4 ......
Got webpage......
Parsing webpage......
Getting http://yhzheng.com:30/text/id?id=3 ......
Got webpage......
Parsing webpage......
Found a illegal url, stop access.
Got a found url.
Got a found url.
Got a found url.
Getting http://yhzheng.com:30/text/id?id=2 ......
Got webpage......
Parsing webpage......
Found a illegal url, stop access.
Found a illegal url, stop access.
Got a found url.
Please wait 4 seconds to show the link graph...
Please wait 3 seconds to show the link graph...
Please wait 2 seconds to show the link graph...
Please wait 1 seconds to show the link graph...
Please wait 0 seconds to show the link graph...
('http://yhzheng.com:30/text/id?id=8', 0.001)
('http://yhzheng.com:30/text/id?id=4', 0.006)
('http://yhzheng.com:30/text/id?id=5', 0.012)
('http://yhzheng.com:30/text/id?id=6', 0.002)
('http://yhzheng.com:30/text/id?id=7', 0.004)
('http://yhzheng.com', 0.001)
('http://yhzheng.com:30/text/id?id=1', 0.014000000000000002)
('http://yhzheng.com:30/text/id?id=2', 0.001)
('http://yhzheng.com:30/text/id?id=3', 0.013000000000000001)
('http://yhzheng.com:30/projects', 0.001)
[FINISH]
```

## License
MIT