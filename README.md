# DIME-infographics
This repository contains code to automate the creation of infographic posters for DIME team's scorecard evaluation in Burkina Faso.

## Data Source
Data for the infographic indicators were collected via interviews with key informants in the municipalities, schools, and district sanitation offices. Responses were recorded using SurveyCTO. The raw survey exports are copied to the `data/raw` folder and include the following `csv` files:

 - `CEB 2014_WIDE.csv`
 - `Directeur Ecole 2014_WIDE.csv`
 - `Directeur Formation Sanitaire 2014_WIDE.csv`
 - `District Sanitaire 2014_WIDE.csv`
 - `Municipalite 2014_WIDE.csv`
 
## Construction of the Infographic Posters
We use [Stata 13 MP](http://www.stata.com/) to clean the data, calculate the indicators, and create JSON-formatted text files describing the layout of the posters. The latter are then read by a short Java script that uses the [Processing.org](https://processing.org/) library to build the infographic images.

### Stata Files
Below are brief descriptions of each of the Stata do-files. We've made liberal use of comments throughout the do-files to explain the program structure/flow.

 - `00_master.do`: this is the master do-file, it sets project globals and runs all component files.
 - `01_clean.do`: this file cleans and merges the raw survey data and outputs it as `merged.dta` in the `data/dta` folder.
 - `02_calculate_scores.do`: this file calculates the indicators values for the infographic posters and outputs `poster1.dta` and `poster2.dta` to the `data/dta` folder.
 - `03_create_JSON.do`: this file converts the indicator data sets to JSON-formatted text, outputting `poster1.json` and `poster2.json` to the `data/json` folder.

### Java Files