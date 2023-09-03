# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
The goal of this project is to determine any possible relationships between bike rentals and venues nearby for the city of Hamilton. This will be achieved by extracting data from Citybikes, Foursquare and Yelp by using their respective APIs and building models using the extracted data.

## Process
### 0. Preparations:
#### &emsp; a. Sign up with Foursquare and Yelp for developer API keys
#### &emsp; b. Set up environment variables for both APIs using newly retrieved API keys

### 1. Extracting data from CityBikes (city_bikes.ipynb):
#### &emsp; a. Query the CityBikes database using the CityBikes API to retrieve entire dataset
#### &emsp; b. Filter the data to keep the data for the city of Hamilton
#### &emsp; c. Convert data into DataFrame format
#### &emsp; d. Format data in the DataFrame
#### &emsp; e. Save DataFrame as CSV file for step 2

### 2. Extracting data from Foursquare and Yelp (yelp_foursquare_EDA.ipynb):
#### &emsp; a. Import CSV file from step 1 and save as a DataFrame
#### &emsp; b. Query the Foursquare database using the Foursquare API and bike station data retrieved from step 1
#### &emsp; c. Convert data into DataFrame format
#### &emsp; d. Format the Foursquare data and filter out irrelevant columns
#### &emsp; e. Save DataFrame as CSV file
#### &emsp; f. Repeat steps b through e, but this time using the Yelp API
#### &emsp; g. Compare the Yelp and Foursquare data to determine which one will be used for step 3 and beyond

### 3. Joining data from step 1 and 2 (joining_data.ipynb):
#### &emsp; a. Import CSV files from step 1 and step 2 (Yelp instead of Foursquare) and save as DataFrames
#### &emsp; b. Merge the DataFrames
#### &emsp; c. Format the data
#### &emsp; d. Drop errenous data entries (such as data where the venue is farther than 1km from a bike stationo)
#### &emsp; e. Drop irrelevant columns
#### &emsp; f. Perform aggregate functions (i.e. counts, averages) on Yelp data after grouping by bike station name
#### &emsp; g. Save formatted DataFrame as an SQLite database file for step 4

### 4. Building the models (model_building.ipynb):
#### &emsp; a. Import the SQLite database file from step 3 into a DataFrame
#### &emsp; b. Display plots for visual analyses
#### &emsp; c. Set up dependent and independent variables (number of bikes as dependent, Yelp data as independent)
#### &emsp; d. Build and fit multiple different models
#### &emsp; e. Display outputs of all the fitted models

## Results
Overall, the Yelp API provided more data over Foursquare as it returned more venues and more information on the venues (such as cost range and user review score). As such, only the Yelp API data was used for data analysis.
As for establishing a relationship between the CityBike data and the Yelp data, the models proved that no straightforward relationoship between the two existed as they either returned low R-squared values or didn't work at all in some instances (the multinomial model didn't even return any numerical results). This all makes sense given that the scatter plots did not show any obvious relationships and the histograms for each observation didn't follow any sort of normal distributions (and weren't consistent with one another). The heatmap of the correlation matrix also showed low correlations between the number of bikes at a station and other variables.

## Challenges 
Besides the challenges of parsing through each of the three APIs to properly retrieve data, format the data and clean the data, the biggest challenge was trying to determine if any relationship could be established between the CityBikes data and Yelp data, especially since the initial hypothesis was that there would be some level of correlation. After conducting several model analyses, it can be concluded that the number of venues, the amount of reviews of a venue on average, the average rating of venues within 1km of a bike station and the average distance from the venues have little to do with the amount of bikes available at each station.

## Future Goals
If it were possible, additional data pertaining to the number of residential areas, offices, schools, roads, alleys, and population could've been implemented as part of the model building as these may have had an impact on the quantity of bikes available at a bike station.
