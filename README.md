# Mission-to-Mars

## Overview of the project:

A web scrapping script was written to obtain informatiom from some astronomy websites with a focus on the planet Mars.

Information was obtained from the following sites:
- [NASA news]('https://data-class-mars.s3.amazonaws.com/Mars/index.html')
- [Mars cartographic online catalog](https://marshemispheres.com/)


## Results:

The webscrapping script collected 4 images along with their titles. The script is designed to retrieve all the images on the page. Beautiful Soup 4 was used to traverse the html file retrieved by Splinter.

2 lists of tags were used to obtain the images's url and their titles. A list of dictionary was needed to store their values in MongoDB so the **zip()** was used to accomplish this as seen below:


```python
for desc, img in zip(title_div, img_div):
        title = desc.find('a').text.strip()
        img_url = img.find('a').find('img').get('src')
        result.append({'title': title, 
                       'url': f'https://marshemispheres.com/{img_url}'})

```
Flask was used to render a page that offers you the option of scrapping these sites and if you choose to do so, some of the contents of these site is retrieved and store in MongoDB. These information is then rendered to you.

## Summary:

A copy of the [final html](view-source_127.0.0.1_5000.html) page produced after using the site to make such a request.