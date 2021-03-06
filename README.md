# Air Polutant Index 2013 - 2015 for Banting
author: WC,L
date: 30 January, 2016

# Introduction

This is a demo of recorded API readings of a place named Banting in Malaysia. The purpose is to determine which hour of a selected month and year has the highest/lowest API reading (Please note that there's no data being captured before August, 2013 and after February, 2015).

This demo is implemented in R, shinyapps and R presentation.

The result from user's input will be a plot demonstrating the changes on recorded API readings per hour.

# The Code

The following are the code that will read the source file, date manipulation and to output a reactive result in a plot.
```{r, eval=FALSE}
  banting <- read.csv("API_Banting.csv")
  banting$Date <- as.Date(banting$Date)
  selected.data <- banting[as.character(year(banting$Date)) == input$year & as.character(month(banting$Date)) == input$month, ]  
  ggplot(data=selected.data, aes(x=Hour, y=API))+stat_smooth(method = "loess", color= "red")+labs(x="Hour", y="API")
```

# The Reactive Output Plot

This is the plot which consist of line that will change according to user's input.
![API vs. Hour](https://github.com/waiching/DevelopingDataProducts/tree/master/api_banting-figure/sample_plot.jpg)

# How to Use the Demo

User will need to select the following input, in order to view the reactive output display - the changes of the API.

- Year
- Month

You may look for the demo version at https://happywc.shinyapps.io/API_Banting/

Source Code located https://github.com/waiching/DevelopingDataProducts