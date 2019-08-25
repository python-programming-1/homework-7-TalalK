import requests
from bs4 import BeautifulSoup
import os


# WIP


url = 'https://www.gocomics.com/pearlsbeforeswine/2019/08/24'




res = requests.get(url)
res.raise_for_status() # URL working or not working, this checks for (404)
soup = BeautifulSoup(res.text)

for i in range(10):
    # find <div id=comic>
    comic_res = requests.get(url)
    comic_div = BeautifulSoup(comic_res.text)

    # find image url
    image_url = comic_div[0].contents[1].attrs['src']
    image_res = requests.get(image_url)
    image_res.raise_for_status()
    
    image = comic_div.select('a[itemprop="image"]')
    image_url = image[0].img.attrs['src'] + '.png'

    # save image url
    image_file = open(os.path.basename(image_url), 'wb') # save just the file image name
    for chunk in image_res.iter_content(100000):
        image_file.write(chunk)
    image_file.close()

    # get prev url
    prev_link = comic_div.select('div.gc-calendar-nav__previous')[0].contents[3]
    comic_url = 'https://www.gocomics.com/pearlsbeforeswine/2019/08/24' + prev_link.get('href')
    print(url)


    
    
    
    
# Trial Code below
'''
# get main website
url = 'https://www.gocomics.com/pearlsbeforeswine/2019/08/24'
while True:
    res = requests.get(url)
    res.raise_for_status()
    soup = BeautifulSoup(res.text)

    # find <div id=comic>
    comic_div = soup.select('div #comic')

    # find image url
    image_url = 'https:' + comic_div[0].contents[1].attrs['src']
    image_res = requests.get(image_url)
    image_res.raise_for_status()

    # save image url
    image_file = open(os.path.basename(image_url), 'wb') # save just the file image name
    for chunk in image_res.iter_content(100000):
        image_file.write(chunk)
    image_file.close()

    # get prev url
    prev_link = soup.select('a[rel="prev"]')[0]
    url = 'https://xkcd.com' + prev_link.get('href')
    print(url)
    sleep(.1)
'''
"""
url = 'https://www.gocomics.com/pearlsbeforeswine/2019/08/24'

res = requests.get(url)
res.raise_for_status()
soup = BeautifulSoup(res.text)

for url in soup.find_all('a'):
    print(url.get('href'))

for div in soup.find_all('img'):
    print(div.img)
"""
