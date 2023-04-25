# Crowd prediction of bus line

Data Science project to predict the crowds over the next 3 days of a bus line in San Sebastian, Basque Country, Spain

![](/readme_images/image1.png)
![](/readme_images/image2.png)

# Introduction
Public transport is a key element to ensure urban mobility and allow citizens to move easily and efficiently in urban areas. However, managing the influx of passengers in public transport is a daily challenge for transport companies. In this context, predicting the number of passengers on bus lines is essential to optimize the planning, management and organization of the public transport service.
In this report, we propose a methodology to predict the number of passengers on bus lines for the next 3 days. For this, we have a historical dataset including the number of passengers per day, per bus line and per type of bus line (day or night) for a period from April 05, 2019 to March 08, 2023. Our The objective is to develop a predictive tool that will enable transport companies to better manage passenger flows by anticipating peak periods and adapting their service offer accordingly.
In this report, we will detail the different steps of our methodology, from preparing the data to modeling and evaluating the results. We will also present the different techniques and algorithms used to predict the number of passengers on bus lines. Finally, we will discuss the results obtained and their relevance for the operational management of transport companies.

# I. Data preparation
We have a history of the daily accumulation of travelers from April 05, 2019 to March 08, 2022, for all the company's bus lines.
The data set is composed of 36,901 observations and 3 original explanatory variables which are, date, bus line and type of bus line (day or night). The quantitative variable to be predicted is the number of passengers/users.
Output tag:
Number of passengers (continuous numeric variable).
First, we sought to visualize our data so that we could hypothetically explain our trends.

![](/readme_images/ml2bus1.png)

We have highlighted here the fact that transport is more busy during the day than at night.
Another graph allows us to highlight the bus most used by travelers.


![](/readme_images/ml2bus2.png)
![](/readme_images/ml2bus3.png)
![](/readme_images/ml2bus4.png)

There is no data recording from March 2020 due to covid. Also post covid data is duplicated for bus types. So we removed them.


![](/readme_images/ml2bus5.png)
![](/readme_images/ml2bus6.png)


We have expanded the data provided by searching other datasets to compare and predict. For this, we looked for data on public holidays in the Pais Vasco region, since public holidays do not have the same effect on public transport as working days. In theory, for example, public transport should be busier and more frequent throughout the day, but not as much as during rush hour. To analyze the effects of public holidays on public transport, we therefore had to find data about them, in particular for the given period from April 05, 2019 to March 08, 2023.
Finding a dataset of public holidays for the Pais Vasco region during the given time period has proven to be difficult as most datasets are from 2021 or later. We finally found an official list published by euskadi.eus, which we used. This list was very short compared to the 2022 datasets we found, so we had to expand it.
For this we thought of another factor, namely football matches, since the San Sebastian football team is very successful in the Spanish league. So we added a dataset containing all home games of this team in the given period. Holidays and football matches usually have an impact on public transport, as theoretically more people use it during these times.
Another factor that can affect public transport, but with fewer passengers, is the weather. So we searched for weather data sets for the given period, but that also turned out to be very difficult. In general, data prior to 2021 requires an expensive subscription. After much research, we finally found a dataset that showed average temperature, precipitation, etc. for each month. Although it wasn't what we hoped to find, it was a good start.
Finally, we realized that the Basque region is famous for its two big clubs, Atlético Bilbao


![](/readme_images/ml2bus7.png)
![](/readme_images/ml2bus8.png)
![](/readme_images/ml2bus9.png)

After researching and collecting the data to compare, the next step was to load and pre-process the data, to ensure that it was in the correct format and that it was clean and error-free. The following steps were used for preprocessing:
- Data cleaning: Removal of missing values, duplicates and correction of errors.
- Feature scaling: Rescale the data so that each feature has a similar scale. Common scaling techniques include min-max scaling, standardization, and normalization.
- Feature engineering: Create new features from existing features that might be more informative for the model. These can be transformations, aggregations or combinations of features.
- Data encoding: Convert categorical data into numerical data. It can be point coding, ordinal coding or binary coding.
- Data Splitting: Split your data into training and testing sets. The training set is used to train the model, and the test set is used to evaluate the performance of the model on new, unpublished data.
Another step in the data mining process, when the end goal is to predict the outcome, is to create visualizations that help understand the outcome and discover the relationships between attributes and the outcome.

Following data visualization tools were used: bar charts, histograms, box plots, correlation matrices, pairwise plots.

![](/readme_images/ml2bus10.png)

The graph below allows us to know the behavior of match days compared to other days.

#II. Modelization
For our models, we initially tested time series but which do not
did not give us interpretable results.
We therefore looked at classic machine learning models such as regression, xgboost and finally an RNN model.


![](/readme_images/ml2bus11.png)

We used for the xgboost, the gridSearch method to find the best parameter. And finally we were able to implement.

![](/readme_images/ml2bus12.png)

For our RNN model, we have the following characteristics:

![](/readme_images/ml2bus13.png)

Finally, we made a prediction over 3 days and had rather interesting results.

![](/readme_images/ml2bus14ml2bus.png)

# Conclusion

Predicting the number of passengers on bus lines is an important issue for
public transport companies. Thanks to our methodology, based on the analysis of historical data and predictive modelling, we have developed a tool which makes it possible to forecast the influx of passengers for the next 3 days with satisfactory accuracy. This prediction allows companies to better manage passenger flows, adapt their service offer according to demand, reduce waiting times and travel times for users, and limit operational costs.
We also highlighted the limitations and perspectives of our approach, which could be improved by integrating additional data, such as local events, weather conditions or school holidays. These future developments could also include more advanced machine learning techniques, such as deep learning, to improve the quality of prediction.
Finally, we are convinced that our methodology for predicting the affluence of passengers on bus lines can have practical applications for the management of public transport in many cities around the world. We hope that our report will be useful for policy makers, transport managers and researchers interested in this important issue for urban mobility.



