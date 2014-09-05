---
title       : Coursera Course Project - Developing Data Products
subtitle    : Would you have survived the sinking of the Titanic?
author      : Matthias Stierle
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---  
<style>
.title-slide {
  background-color: #EDE0CF; /* #EDE0CF; ; #CA9F9D*/
}

.title-slide hgroup > h1{
 font-family: 'Oswald', 'Helvetica', sanserif; 
}

.title-slide hgroup > h1, 
.title-slide hgroup > h2 {
  color: #535E43 ;  /* ; #EF5150*/
}
</style>
## Basic idea

- Choose one of the example R data sets that is suitable for making predictions

### Summary of Titanic data set


```
##   Class       Sex        Age     Survived      Freq      
##  1st :8   Male  :16   Child:16   No :16   Min.   :  0.0  
##  2nd :8   Female:16   Adult:16   Yes:16   1st Qu.:  0.8  
##  3rd :8                                   Median : 13.5  
##  Crew:8                                   Mean   : 68.8  
##                                           3rd Qu.: 77.0  
##                                           Max.   :670.0
```
&#8594; Predict whether one would have survived the sinking of the Titanic

--- .class #id 
## Choose a learning algorithm
- As all the predictor variables (Sex, Age and Class) are factors we can make use of a rule-based algorithm.
- Therefore we choose naive bayes contained in the e1071 package

#### Load Package and built classifier

```r
library(e1071)
classifier <- naiveBayes(Survived ~ ., data = Titanic)
```
#### Example

```
##   Class  Sex   Age
## 1   1st Male Child
```
#### Predict on example

```r
predict(classifier,example)
```

```
## [1] Yes
## Levels: No Yes
```


--- .class #id 
## Layout
### Sidepar Panel
- A sidepar panel for defining the 3 input variables: Sex, Age and Class
- A dropdown for class as we have more than 2 options
- Radio Buttons for Sex and Age as we have only 2 options for each

### Main Panel
- A short description of the app
- A short documentation/manual how to use the app
- The result of the prediction including an image

--- .class #id 
## The result

- The app can be found on https://supamuc.shinyapps.io/myApp/

<img src="shark_screenshot.png" align ="center" alt="Drawing" style="width: 800px;"/>
