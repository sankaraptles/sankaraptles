---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_What_is_this
title: "Visualization of Cryptocurrency Price Change (BTC)"

# post specific
# if not specified, .name will be used from _data/owner/[language].yml
author: Sankara Rama Pandian S
# multiple category is not supported
category: R Analysis
# multiple tag entries are possible
tags: [R, Data Visualization, cryptocurrency]
# thumbnail image for post
img: ":btc.png"
# disable comments on this page
#comments_disable: true

# publish date
date: 2023-04-19 11:45:34 +0900

# seo
# if not specified, date will be used.
#meta_modify_date: 2022-01-01 10:04:30 +0900
# check the meta_common_description in _data/owner/[language].yml
#meta_description: ""

# optional
# please use the "image_viewer_on" below to enable image viewer for individual pages or posts (_posts/ or [language]/_posts folders).
# image viewer can be enabled or disabled for all posts using the "image_viewer_posts: true" setting in _data/conf/main.yml.
#image_viewer_on: true
# please use the "image_lazy_loader_on" below to enable image lazy loader for individual pages or posts (_posts/ or [language]/_posts folders).
# image lazy loader can be enabled or disabled for all posts using the "image_lazy_loader_posts: true" setting in _data/conf/main.yml.
#image_lazy_loader_on: true
# exclude from on site search
#on_site_search_exclude: true
# exclude from search engines
#search_engine_exclude: true
# to disable this page, simply set published: false or delete this file
#published: false
---
<!-- outline-start -->

This is a blog on Visualization of Cryptocurrency Price Change (BTC) using R Programming Language.

<!-- outline-end -->

#### Introduction

In recent years, cryptocurrency has gained popularity as a kind of investment, with Bitcoin (BTC) being the most well-known type. Since its creation in 2009 under the pseudonym Satoshi Nakamoto by an unidentified individual or group, it has drawn considerable interest from investors, traders, and companies all around the world. Bitcoin has had a very unstable value, making it a hazardous but possibly lucrative investment.

This analysis tries to offer a thorough examination of how the price of BTC has changed over time, using a variety of visuals to help understand market trends. The information utilised in this research comes from a CSV file on Kaggle that includes daily Bitcoin values from July 2010 through March 2023.

This analysis has three different goals in mind. In order to better comprehend how Bitcoin has performed over time, it is first necessary to provide bitcoin pricing data in a clear and straightforward manner. Second, to find patterns, trends, and anomalies in the bitcoin market and offer information for making wise investment choices. In order to stay informed of market developments, the third step is to look at ways to send out alerts and notifications for substantial price changes or changes in trade volume. 

We will utilise the R programming language to handle and analyse the data in order to accomplish these goals. In order to present the data in a clear and understandable way, we will develop a variety of visualisations, including line graphs, candlestick charts, and heatmaps. To acquire a deeper understanding of market movements, we will also employ statistical analytical tools including moving averages and volatility analysis. 

The report seeks to present a thorough analysis of BTC's price movements over time and to pinpoint market possibilities and risks. It will offer information that traders, corporations, and investors may utilise to decide wisely about their Bitcoin investments.

#### Overview

In order to comprehend how various cryptocurrencies have performed over time, spot trends, patterns, and anomalies in the cryptocurrency market, and gain knowledge for making wise investment choices, the study of cryptocurrency prices entails the visualisation of data.

Several visualisation methods, such as line charts, candlestick charts, scatter plots, or heatmaps, can be utilised to accomplish these goals. The choice of visualisation depends on the research questions and the features of the data and can help to expose various aspects of the data.

A general description of the data set, including the time period covered, the number of cryptocurrencies included, and any pertinent statistics like daily trade volume, is usually given before the research gets started. This aids in setting the scene for the study and reveals any biases or data restrictions that might exist.

Following that, trends and patterns in the cryptocurrency price data are found and examined. This can include long-term price trends, cyclical patterns, or sharp price increases or decreases. It is also possible to look at correlations or causal relationships between various cryptocurrencies or between the values of cryptocurrencies and outside variables like market mood, legislative developments, or macroeconomic events.

Analysis of cryptocurrency prices can provide information for making investing decisions. Noteworthy patterns or trends can point to possible hazards or investment possibilities, such as inexpensive cryptocurrencies, prospective market bubbles, or abrupt price changes that could signify market turbulence. Investors can use this information to decide which cryptocurrencies to buy and when to enter or depart the market.

The analysis has effects on risk management in cryptocurrency investments as well. It is possible to identify potential threats or dangers to investment portfolios and explore risk management techniques like diversification, hedging, and stop-loss orders.

An effective tool for researching the cryptocurrency market and selecting an investment is the visualisation of cryptocurrency values. Investors may manage the intricate and turbulent crypto market with the insights gathered from the analysis, reducing risk exposure. In continuing to hone and improve the analysis over time, it is crucial to recognise the limitations of the data and the visualisation methods employed.

#### Visualization of Cryptocurrency

A crucial technique for evaluating the success of various cryptocurrencies is the visualisation of cryptocurrency prices. Making wise financial decisions can be aided by the use of visualisations, which can help to spot market trends and patterns. Also, it can be used to monitor variations in trading volume, which is useful for gauging market sentiment and spotting possible business possibilities. The historical price data of Bitcoin (BTC) will be analysed using a variety of visualisations in this report to give us an understanding of how this cryptocurrency has performed over time. We'll look at various visualisation strategies and talk about how they affect our understanding of cryptocurrency pricing. This analysis will be helpful for both investors and researchers in the cryptocurrency industry because it will give them a deeper grasp of market trends and patterns as well as possible upcoming changes.

We must first load the essential libraries in order to carry out the visualisation. In this instance, we are use the gridExtra, reshape2, and ggplot2 packages. With R, ggplot2 is a well-liked library for building intricate visuals, and reshape2 aids in reorganising data frames to make charting easier. For integrating numerous plots, use the gridExtra library.


{% highlight python %}
# Load the required packages
library(tidyverse)
library(lubridate)
library(plotly)
library(ggplot2)
library(htmlwidgets)
library(reshape2)
{% endhighlight %}


The read.csv() function is then used to read the CSV file containing the cryptocurrency price information. The data from a CSV file is read into a data frame using the read.csv() function. The CSV file in this instance is called BTC.csv. The first row of the CSV file's header row should contain the column names, as indicated by the header = TRUE option.


{% highlight python %}
# Read in the BTC cryptocurrency price data
btc_prices <- read.csv("C:/Users/Sankar/fakepath/BTC.csv")
 
# Convert the date column to a date format
btc_prices$date <- ymd(btc_prices$date)
{% endhighlight %}


In order to match the column names indicated in the query, we finally rename the columns of the btc prices data frame. With R's colnames() function, complete this step. It is simpler to deal with the data and the code is more intelligible when the column names are changed.

Setting up the data and libraries required for the visualisation process requires all of these preliminary steps to be completed.

##### Line Chart

Line charts are a popular visual analysis method for studying cryptocurrency price data. They are helpful for showing a cryptocurrency's historical price data over time. Line charts make it simple to see trends and patterns in the price data by putting the prices on a graph.

Line charts are especially helpful for spotting long-term market patterns. It is possible to find trends that can be applied to make wise investment selections by looking at past price data over a period of months or years. A cryptocurrency may be an excellent investment opportunity, for instance, if its price has been gradually rising over a lengthy period of time.

Moreover, line charts can be used to spot brief market gyrations. You can analyse the price data over a shorter time frame, such days or weeks, by zooming in on the chart. This can assist in identifying short-term market trends and patterns, such as price peaks or troughs.


{% highlight python %}
# Create a line chart of BTC prices over time
btc_line_chart <- btc_prices %>% 
  plot_ly(x = ~date, y = ~close, type = 'scatter', mode = 'lines', 
          name = "BTC Close Prices") %>% 
  layout(title = "Bitcoin Close Prices Over Time",
         xaxis = list(title = "Date"),
         yaxis = list(title = "Price (USD)"))
{% endhighlight %}


The code above generates a line chart that shows the historical close prices for BTC (Bitcoin). The R plotly library is used to create the chart. The date is represented by the chart's x-axis, while the close price of BTC in USD is shown on the y-axis. Using the layout option, the chart is titled "Bitcoin Closing Prices Over Time." The graph shows the performance of BTC over time in an easy-to-understand manner, enabling us to spot trends, patterns, and anomalies in the cryptocurrency market. We may make wise investment selections and keep track of big price fluctuations or changes in trade volume by viewing the data in this way. Investors who are interested in trading cryptocurrencies and who want to keep track of how various cryptocurrencies have performed over time will find this chart to be helpful.

![Line Chart](:Rplot001.png){:data-align="center"}

From July 2010 through March 2023, the daily closing prices for Bitcoin (BTC) are shown on a line graph. The dates are represented on the x-axis, and the y-axis displays the price of BTC in USD.

The data shows that, between 2015 and 2017, the price of bitcoin was largely constant, with sporadic price increases. Yet towards the end of the year, there was a sharp increase in price, and in December 2017, BTC hit an all-time high of around $20,000 USD. After reaching its high, the price of BTC fell precipitously, and it’s worth significantly decreased throughout 2018.

Early in 2020, BTC underwent a period of largely steady development with a few minor price changes. However, the price abruptly dropped in March 2020, right about the time the COVID-19 epidemic started. BTC's price immediately recovered, rising to almost $28,000 USD in December 2020, its highest level since the peak in 2017.

The line graph demonstrates the overall volatility of BTC prices over time, with notable price swings and sporadic periods of stability. It is significant to remember that past results are not necessarily indicative of future outcomes, and it is not advised to base investment decisions simply on historical trends.

##### Candlestick Chart

A common financial chart used to show price movement of an asset, including cryptocurrency, is a candlestick chart. For traders and investors, it is a handy tool for examining an asset's price movement over time. The candlestick chart displays the opening, closing, high, and low prices of a security or asset for a particular time period.

The candlestick chart is made up of several bars, each bar indicating a certain period of time (such as a day or an hour). A "body" and two "shadows" or "wicks" make up each bar. The shadows indicate the high and low prices for that period, while the body shows the gap between the opening and closing prices.

Candlestick charts are helpful for identifying important levels of support and resistance as well as for illustrating trends and patterns in price movements. They can also be used to spot particular chart patterns that could indicate future changes in price movement.

Candlestick charts are very helpful when discussing cryptocurrency because of the high volatility and often fast price fluctuations that characterise these markets. Candlestick charts can help traders and investors understand market emotion and make wise trading decisions.


{% highlight python %}
# Create a candlestick chart of BTC prices
btc_candle_chart <- btc_prices %>% 
  plot_ly(x = ~date, open = ~open, high = ~high, low = ~low, close = ~close,
          type = 'candlestick', name = "BTC Candlestick Prices") %>% 
  layout(title = "Bitcoin Candlestick Prices",
         xaxis = list(title = "Date"),
         yaxis = list(title = "Price (USD)"))
{% endhighlight %}


The code mentioned above is used to make a candlestick chart of the price of Bitcoin. The code makes use of the btc prices data frame, which holds details on BTC prices, including the date, the high price, the low price, the opening price, and the closing price. It then uses the plot ly() function from the plotly library to produce a candlestick chart. The open, high, low, and close parameters are set to the corresponding columns in the data frame, while the x parameter is set to the date column.

The generated graph makes it easy to understand how BTC's price has changed over time. The candlesticks display the opening and closing prices in addition to the price range over a specified time period. Making educated investing decisions can be aided by using this sort of chart to spot trends, patterns, and anomalies in the price movements of cryptocurrencies.

We can see that each candlestick in the BTC candlestick chart produced by the aforementioned R code indicates the price range of BTC over a period of years. The "wick" or "shadow" of the candlestick reflects the price range between the highest and lowest price of BTC for that day, while the "body" of the candlestick shows the opening and closing prices of BTC for that day.

![Candlestick Chart](:Rplot002.png){:data-align="center"}

The chart shows that during the time period covered by the dataset, there were large variations in the price of BTC. There are times when there is substantial growth and times when there is decrease. For instance, we can observe a significant decline in the price of BTC around the middle of March 2020, which corresponds with the start of the COVID-19 epidemic. In late 2020 and early 2021, we may also expect to witness a big increase in the price of bitcoin, which corresponds with a rise in institutional use and general acceptance of cryptocurrencies.

##### Heatmap

Heatmaps are frequently used in data visualisation to present complex data in a condensed and clear manner. A heatmap can be used to display the price changes for several cryptocurrencies over time in the context of cryptocurrency price visualisation. The price of a specific coin at a specific time is shown in each heatmap cell.

For finding patterns and trends in sizable datasets, heatmaps are helpful. It is simple to rapidly spot areas with high and low values, and to see how these values vary over time, by utilising color-coding to represent values.

Heatmaps can be used to contrast the price movements of various cryptocurrencies in addition to showing price changes for numerous cryptocurrencies. Investors and traders who want to find correlations between various cryptocurrencies or figure out which cryptocurrencies are performing well in comparison to others may find this to be helpful.


{% highlight python %}
# Reshape the data for the heatmap
btc_data_melted <- melt(btc_prices, id.vars = "date", measure.vars = "close")
 
# Create a heatmap of BTC closing prices over time
ggplot(data = btc_data_melted, aes(x = date, y = variable, fill = value)) + 
  geom_tile() +
  scale_fill_gradient(low = "#FFEDA0", high = "#E31A1C", name = "Closing Price") +
  scale_x_date(date_breaks = "1 year", date_labels = "%Y") +
  labs(title = "BTC Closing Prices Heatmap", x = "Year", y = "Day of Year") +
  theme(plot.title = element_text(hjust = 0.5))
{% endhighlight %}


The aforementioned code generates a heatmap to show the evolution of BTC closing prices. Using the melt function from the reshape2 package, which changes the data's wide format to long format, is the initial stage in data reshaping. The ggplot function needs the data to be in a specified format, therefore this is required.

The heatmap is then produced using the ggplot tool. The date column is mapped to the x-axis using the aes function, the day of the year is mapped to the y-axis using the variable column, and the closing price is mapped to the fill colour using the value column. The heatmap's tiles are made using the geom tile function. The heatmap's colour scheme is set using the scale fill gradient function, with low values represented by the colour yellow (#FFEDA0) and high values by the colour red (#E31A1C). The x-axis labels on this graph are formatted as years (%Y) using the scale x date function. The plot is embellished with a title and axis labels using the labs function, and the title is centred using the theme function.

![Heatmap](:Rplot003.png){:data-align="center"}

The grid-based heatmap displays the BTC closing prices over time. The y-axis displays the day of the year, while the x-axis displays the year. Each square's colour intensity represents the closing price of Bitcoin on that specific day.

The graph illustrates the sharp rise in Bitcoin prices from 2014, with the greatest values recorded in 2017 and early 2018. The BTC market has a strong seasonality, with prices often rising in the second half of the year and falling in the first half of the following year.

The heatmap uses a yellow to red colour scale, with yellow representing lower closing prices and red representing higher closing prices. The closing price range for each hue is displayed in the heatmap's legend, which is located on the right side of the chart.

According to the heatmap, there have been multiple instances of severe volatility in Bitcoin prices over the years, with significant price swings occurring quickly. We can also see that the price of bitcoin has been rising overall, fluctuating between periods of rapid growth and periods of correction.

##### Scatter Plot

A scatter plot is a graph that shows how two numerical variables relate to one another by arranging the variables as dots on a two-dimensional plane. Each dot represents a single observation, and the values of the two variables it stands for decide where it is. The nature and intensity of the link between two variables, such as the price and trading volume for a particular cryptocurrency, can be explored using scatter plots.

Scatter plots can be used to investigate the link between several characteristics of a cryptocurrency, such as its daily opening price and trading volume, in the context of displaying cryptocurrency values. Investors can understand market trends and spot potential possibilities for profitable investments by visualising these relationships.

Scatter plots can also be used to spot trends and patterns in the data, like outliers or groups of related data points. Analysts can make educated investment judgements by analysing the scatter plot to discover whether there is a positive, negative, or no connection between the two variables.



{% highlight python %}
# Create scatterplot of high and low prices
btc_scatter <- ggplot(btc_prices, aes(x = high, y = low)) +
  geom_point(alpha = 0.5) +
  labs(x = "BTC High Price", y = "BTC Low Price", title = "Scatterplot of BTC High and Low Prices")
{% endhighlight %}


The aforementioned code generates a scatter plot to show the correlation between the high and low prices of Bitcoin. The plot was made using the ggplot function from the ggplot2 package.

The variables to be plotted on the x and y axes are supplied as "high" and "low," respectively, in the aes() function. The scatter plot is made using the geom point function, and the alpha option is set to 0.5 to modify the transparency of the points. The x and y axis labels as well as the plot title are set using the labs() method.

Finding any patterns or trends between the high and low prices of BTC can be done with the help of this scatter plot. For instance, we would anticipate seeing a general upward trend in the scatter plot if there is a positive connection between the two variables. On the other hand, we would anticipate to find a random distribution of points if there is no association or a negative correlation. Overall, the relationship between the high and low prices of BTC is quickly and graphically summarised by this plot.

![Scatter Plot](:Rplot004.png){:data-align="center"}

The scatter plot demonstrates that the high and low prices have a positive linear relationship, which means that as the high price rises, the low price also tends to rise. We can also observe that there is a wide range of high and low prices, with some times having a very little gap between the high and low prices and other eras having a significantly higher difference.

Furthermore, we can observe that the high and low prices of BTC have a positive linear relationship. This implies that the low price tends to rise as the high price does as well. The spread of the points, however, highlights the fact that there is a significant amount of variability in the relationship between the two variables.

#### Findings

The following conclusions can be drawn from an analysis of Bitcoin (BTC) price movements using various visualisation approaches. BTC values have fluctuated considerably over time, exhibiting both high volatility and a long-term increasing tendency. The candlestick chart offers a more in-depth look at price fluctuations and trends within shorter time frames, while the line chart clearly displays the general trend in BTC prices. The scatter plot of the BTC high and low prices shows a strong positive correlation between them, indicating that the lows grow in tandem with rising BTC values. A more thorough perspective of price changes and patterns is provided by the heatmap of BTC closing prices over time, which also makes obvious when volatility has grown.

The line graph demonstrated that, since its launch in 2009, the price of Bitcoin has dramatically climbed. Even if there have been times when prices have fallen, this is not the long-term tendency. The candlestick chart also revealed that there have been times of volatility for Bitcoin, which can be ascribed to shifts in market demand, world events, and legal developments. The scatter plot revealed a significant positive connection between the high and low prices for Bitcoin, demonstrating that when the high price is present, the low price is frequently present as well. For investors who seek to forecast the price range for a specific time period, this result may be helpful. The heatmap showed that there is a seasonal pattern to the price of bitcoin. The first quarter of the year has a higher concentration of increased prices, while the second quarter typically sees a decline in prices. With a few exceptions, this pattern has persisted throughout time. The candlestick chart demonstrated that geopolitical tensions, economic policies, and governmental laws all have an impact on the price of bitcoin. As an illustration, prices drastically decreased in 2018 as a result of regulatory crackdowns in China, South Korea, and other nations.

Investors and traders may find it easier to analyse BTC price fluctuations and spot lucrative chances with the aid of these visualisation approaches. The data demonstrates that Bitcoin is a very sensitive and volatile asset, with prices influenced by a variety of variables. For investors and traders who wish to forecast Bitcoin prices and make wise decisions based on market trends, the findings may be helpful.

#### Conclusion

Using a variety of visualisation tools, the research of bitcoin values has produced some intriguing findings. The price of BTC has been rising over time, but with a lot of volatility, as shown by the price line chart. The daily price swings are shown in greater detail on the candlestick chart, with red candles denoting a decline and green candles denoting an increase. The high and low-price scatter plots demonstrate a positive connection between the two variables, demonstrating that when the high price rises, the low price typically follows suit.

A visual picture of price patterns over the course of the year is provided by the heatmap of BTC closing prices over time. It demonstrates that the price of BTC often rises in the first half of the year, peaking in May, before falling in the second half. The heatmap also reveals that BTC prices peaked in 2017 and declined somewhat in 2018 and 2019.

These visualisations bring to light the erratic nature of bitcoin values as well as the significance of comprehending the fundamental trends and forces at work. Cryptocurrency might be a high-risk investment, but for those who are ready to accept the chance, it can also yield big benefits. Before making any investing selections, it is crucial to carry out careful research and analysis.
