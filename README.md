
# E-commerce-customer-reviews-extraction

# Objective:
To create a dataset where a product's specifications, cost, ratings are colocated along with the reviews from various E-commerce sites.

# Goal:
This dataset helps in analysing the reviews for a product collected from various E-commerce websites. Sentimental analysis or any other analysis can be done more accurately as the reviews are not biased for any website. 

The gist made from the analysis of all the reviews will make the buyer more informative about the product to make his/her decision.

This dataset can also be used to compare various products of the same category as all the specifications of the product are being listed.

If a buyer from E-commerce site wishes to go for a new product released in the market, where there is no scope for its working reviews, this dataset helps him/her to find the similar product if any was released  before from any other brand, and can be aware of the problems/advantages it gave to customers and helps buyer to make his/her decision.

# Tools/softwares used:

Python

Selenium

Beautiful Soup

Chromedriver 

# Approach/methodology
We chose mobiles as the category for this project. We did scrape all the relevant information for mobiles needed from couple of websites named flipkart.com and 91mobiles.com
1. Flipkart:

The Flipkart E-commerce site is of dynamic webpages which is highly developed.

To scrap the information for each mobile, we need to go to the respective url for that mobile, which manually takes time. So we automated this using selenium and wrote a python script(Flipkart_reviews.ipymb), which did the job for us.
# Plan for flipkart:

we send the input to search key as "smartphone" through the script, which listed all the phones with almost 217 pages.

we collected name,link,ratings from these pages and stored in a dictionary with name as the key and rest in a list as value

we looped over this dictionary where each element has link to its respective page. Likewise we automated the process to open each page and collect information like all the specifications for that specific mobile phone. For reviews, we made a list and appended each review to it. Reviews are spread over various pages, so we again looped to every page and collected all the reviews in that page and stored in a list which inturn stored as a value for key"reviews" in the product's specific dictionary.

So all the products information is present in their corresponding dictionaries and we appended this as a write operation into a json file. 

All the loops are controlled by selenium and chromedriver

This file finally contains all the information for each mobile phone in json format.

2. 91mobiles.com:

91mobiles.com is also an E-commerce website , where we can find the reviews for the product from amazon. This is a dynamic website, which is highly developed. This is a javascript webpage

# Plan for 91mobiles.com:
Here, the mobile phones are categorized according to their brands. So we used that as an advantage.

We scraped and collected the links for the brands along with brand names.

we looped over each brand link to get all the phones in that brand, here we collected individual mobile's information such as link for the mobile, along with mobile name. This is stored in a dictionary with mobile's name as the key.

we looped over this dictionary to open the mobile's respective page, and scraped information like rating and how many users did gave the rating.

For reviews, how many did find this review useful, as we are interested in amazon customer reviews, we found the filter element and sent keys "Amazon.in".

All the reviews, useful count are collected into a dictionary and wrote these dictionaries as json into a file.

Reviews are not in pagewise format, rather in a dynamic scroll type. so we used selenium to scroll the current web page to scrap the reviews. 

All the loops are controlled by selenium and chromedriver.

# Data integration:

The data inserted was not in proper format, so we converted it to string and added few keys to make into a proper jsons structure.

Then we converted all the string back to json.

Changed the keys of json's dictionary from numbers to the product's name.

junk characters from price column and name column are removed and replaced respectively.

Repeated all the above steps for amazon dataset aswell.

the two new datasets are merged basing on their names

stored the merged dictionary into a json file

converted json structure to csv using pandas dataframes where nulls are inserted for attributes absent for respective phones.

Final csv and json merged datasets are generated.

# Challenges faced:

1. Flipkart is a commercial e-commerce website, where the filter to primarily fetch phones according to their brands was in their home page. We developed our code to scrap according to the structure, But as it is a commercial website, there was a sale happening on dec 1st and entire structure has been re-formatted from their end for sale. This made us to use another approach for fetching the mobiles, that was by search key.

2. In 91mobiles, the reviews we can get by scrolling the page, which was quite a new task and we achieved it with selenium.

3. While scraping, there was a high chance where site used to block us. If we focus on creating a single dictionary and store each element as a product, when it fails, all the stored information was locked and went of no use. So we followed a method to append each element to the file once it is done.

4. This append further created a problem, as the file which gets individual dictionaries is not in a json format as the append just adds to the end of the file.
--> we did convert the whole file to a string and and individually looped over a pattern and added numbers as the key to it. So it was into json format.

5.There are some junk characters in price like Indian rupee symbol which are hidden and not being able to remove. Need to research more on how to remove them

6. Limitation: We can scrap from various sites but as these E-commerce sites are commercial, we are not allowed/authorized to scrap.


# Attribute name and its definition:

name: It gives the name of the product.

price: Information about the sale price of the product.

rating: overall rating for a product given by users.

reviews: This key gives information about reviews from main website, for us it is flipkart.

amazon reviews: This key gives the reviews collected for that product from amazon users. along with information like how many found the corresponding review useful. This gives the weightage for the review.

All the specifications are individually placed in below attributes.
'3G': whether 3G compatible(Yes/No)

Audio Formats: various audio formats supported

Bluetooth Support: whether bluetooth is supported(Yes/No)

Bluetooth Version: Version of Bluetooth

Browse Type: Category of the product

Color: Color of the product:

Depth: depth of the phone

Display Size: size of the display for phone

Dual Camera Lens: which camers plays important role in dual camers

Flash: description about flash

Frame Rate: Video frame rate for mobile

Full HD Recording: whether cmpatible for HD recording

Graphics PPI: PPI for graphics in the phone

Height: Height of the phone

Hybrid Sim Slot: whether phone has Hybrid sim slot(Yes/No)

In The Box: What does the closed box contains

Internal Storage: Internal storage for the phone

Internet Connectivity: Various bands supported for internet in the mobile

Model Name: Model name of the phone

Model Number: Model number of the phone which is unique.

NFC: whether NFC is supported(YES/NO)

Network Type: Various network types supported

OTG Compatible: whether phone is OTG compatible

Operating System: operating system installed

Optical Zoom: Optical Zoom availability(YES/NO)

Other Display Features: Other display features of the phone like contrast ratio etc.

Other Features: Other features of the phone

Phone Book: availability(Yes/No)

Pre-installed Browser: Pre-installed web browser

Primary Camera: lens for the rear camera

Primary Camera Features: various highlighted features of primary camera

Processor Type: Type of processor used

Removable Battery: availability(Yes/No)

Resolution: Resolution in pixels

Resolution Type: Display type

SAR Value: features of SAR value

SIM Size: various sizes of sim's supported

SIM Type: categories of sim's that can be used

Secondary Camera: lens of front camera

Secondary Camera Features: various features of secondary camera

Sensors: Various sensors available

Series: series of phone from that brand

Speaker Phone: Availability(YES/NO)

Supported Languages: various languages supported

Touchscreen: availability(Yes/No)

Video Formats: various video formats supported by phone

Video Recording: availability(Yes/No)

Warranty Summary: warranty provided by company

Weight: weight of the phone

Wi-Fi: availability(YES/NO)

Wi-Fi Version: version of wi-fi

Width: width of the phone



# Conclusion:

Final datasets we produce are three, where in two for exclusively flipkart and amazon, other is the dataset where phones contain both amazon and Flipkart reviews.

This dataset can be used in various ways. It is a pool of information for the specific phone.

flipkart_data(JSON)--contains all the phones which are scraped from flipkart site with name as their key.

amazon_data(JSON)--contains all the phones which are scraped from 91 mobiles site with name as their key and amazon reviews in their values.

flip_amz(JSON)--contains the phones which are in both the datasets, and having both the reviews from flipkart and amazon.

FLIPKART_AMAZON_CSV_FILE(CSV)-- contains the phones which are in both the datasets, and having both the reviews from flipkart and amazon. There are various attributes for different phones, so NULL's are inserted for no value.

# Future Work:

Need to analyze all the reviews for a particular smartphone by using various methods like text analytics and sentimental analysis with the help of natural language processing a final verdict or overall review should be given for the specific phone which covers the gist of almost all the customer reviews. This will help the customer to make his decision quicker than going through several reviews and being ended up in mess.















