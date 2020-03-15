# BATTLE OF NEIGHBOURHOODS

If you are trying to start your own business say it can be a coffee shop, a restaurant, a cocktail bar, etc. which will be the best location to set up your business?

There are several steps you should consider before you start your business, starting from making a plan, Planning your Finances, Choosing the best Bussiness Structure, Getting Licences and Permits, Choosing the right location to start your business and promoting your business.

I am sure you will have all the steps covered with the business idea you get, but Selecting a location to start your business can be tricky and should be selected carefully.

You should check the competition from other vendors along with growth potential, accessibility, cargo needs, and other costs.

In this project, I tried to have a closer look at the other competitors in all the available neighborhoods of a given city. With these insights one can decide on the location to choose where business can be.

Given a city, I can segment it into different neighborhoods using the geographical coordinates of the center of each neighborhood

Using a combination of location data and Machine Learning we will group the neighborhoods into clusters.

I have used Foursquare API as the location data provider

# Exploring and Clustering the neighborhoods in Toronto.

I have considerd that I wanted to start my bussiness in the city of Toronto

In this project, I will explore, segment, and cluster the neighborhoods in the city of Toronto. However, the neighborhood data is not readily available on the internet. 

For the Toronto neighborhood data, a Wikipedia page exists that has all the information we need to explore and cluster the neighborhoods in Toronto. I have scraped the Wikipedia page and wrangled the data, cleand it, and then read it into a pandas dataframe so that it is in a structured format.

Following Wikipedia page, https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M, was used to extract and scrape Toronto Neighborhood data using various Python packages. 
Next, I have extracted the geographical coordinates of the neighborhoods from "http://cocl.us/Geospatial_data" that gave us data of the Latitude and the Longitude for the Neighborhoods. With a list of Neighborhoods and their Latitudes and Longitudes, I have used Foursquare API to get venue information and I have selected the Venue category for further analysis. I have used K-mean Clustering (Machine Learning Technique) to determine suitable locations for our new business as well as Folium library to locate them in the Map. The processing of data will help us identify which neighborhoods are densed with which venue, therefore, indicating a suitable location to open a new one


## Cleaning the data
I have Removed the rows  with a borough that is "Not assigned".

It can be noticed that more than one neighborhood can exist in one postal code area. For example, in the table on the Wikipedia page, you will notice that M5A is listed twice and has two neighborhoods: Harbourfront and Regent Park. These two rows are combined into one row with the neighborhoods separated with a comma 

If a cell has a borough but a Not assigned neighborhood, then the neighborhood will be the same as the borough.

Once that we have built a dataframe of the postal code of each neighborhood along with the borough name and neighborhood name, in order to utilize the Foursquare location data, we need to get the latitude and the longitude coordinates of each neighborhood.

The dataframes are then joined based on the postal code. The dataframe looks like this:
![image](https://user-images.githubusercontent.com/46058709/76485526-bf3a7d80-63ea-11ea-960c-6d0ee96d7afa.png)

### Exploring and clustering the neighborhoods in Toronto.

I have used Folium to have visualization of all the neighbourhoods.
The below image shows the neighborhoods of all the neighborhoods
![image](https://user-images.githubusercontent.com/46058709/76485649-1b9d9d00-63eb-11ea-9f1d-1cf862a90e8d.png)


##### Note: To be more specific I have concentrated only on boroughs that contain the word Toronto, this reduces my area of interest and the points in the neighborhood. 

New Neighborhoods image
![image](https://user-images.githubusercontent.com/46058709/76485883-c1e9a280-63eb-11ea-928f-1a1bbfad54f5.png)


##### I have used Foursquare API to explore the neighborhoods
Using the Foursquare API top 100 Venues with a radius of 200 meters are extracted for all the neighbourhoods.I have checked the venues that are returned by each neighbourhood.The below image shows the same.
![image](https://user-images.githubusercontent.com/46058709/76486214-b64aab80-63ec-11ea-8f56-73fd0037b237.png)

There were 232 unique categories in total

### Analyzing Each Neighbourhood
I have encoded each Venue category and grouped the rows by neighbourhood and have taken mean of frequency of occurence of each category

Using this I have created a dataframe that displays top 10 venues for each Neighbourhood

# Clusterinig the Neighborhoods

I used K-means Clustering to cluster the neighborhoods

The dataframe created was :
![image](https://user-images.githubusercontent.com/46058709/76486409-3ffa7900-63ed-11ea-9d4c-4ce889460e91.png)

I have added the cluster labels to the data before merging it with actual data, Again i have used Folium to visualize the clustered data.
![image](https://user-images.githubusercontent.com/46058709/76486753-52c17d80-63ee-11ea-8cf3-b8f101d22ce2.png)

Now we have our clusters ready. And For our bussiness if we want to check which bussiness to start in 'Rosedale' Neighbourhood, but we want to check which venue to start, the following dataframe gives us an idea of most common venues in our desired neighbourhood.

![image](https://user-images.githubusercontent.com/46058709/76712406-9a921e80-66e6-11ea-963a-5110da6ceee2.png)

We can clearly see the most common venues in the given Neighborhood, based on these results we can plan on which venue is best to start a new bussiness.

We can also look into similar Neighbourhoods which has same characterstics of the above checked neighbourhood, since the neighbood of our choice belongs to cluster 0, we can check the other neighbourhoods belonging to the same cluster, which gives us a better idea about other neighbourhoods befor making the final decision.

![image](https://user-images.githubusercontent.com/46058709/76712415-b3023900-66e6-11ea-8a74-e82078540917.png)

NOTE: In this project I have considered the way we can look at the venues in the given neighbourhood before setting up a venue of our own. It should be noted that they are many other factors which should be consired before making a final decision.
