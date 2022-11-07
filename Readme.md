# Capstone Project - Football Pass Analysis using KMeans Clustering

## Problem Statement
I represent the Football Association of Singapore, who are looking to invest actively in womens football locally. With the recent win in Euros 2022, the England women’s football team have improved rapidly, in the last few years. I’ve selected this team to study their improvement points in order to provide more insights to our local national team. Their passing statistics are highlighted as a key point to their success, and this presentation will cover my analysis of their passes using KMeans clustering.

--- 
## Data Source
Statsbomb is a UK-based football analytics and data visualisation company introducing common data analytics practices seen in business and tech to the world of football analytics. They provide free event data (limited) to the public for analysis purposes, and invite research papers every year to discover new ways of interpreting data. Event data captures all of the action that the players perform with the ball, and includes passes, dribbles, crosses, interceptions, tackles, shots, etc.

We will be using the passing data for analysis.

---
## Executive Summary
**INTRODUCTION**
I’ve shortlisted 2 tournaments, World Cup 2019, and Euros 2022, to compare England’s different styles of play in the 2 events.
For reference, England lost to USA 1-2 in the semis in World Cup 2019, and won the Euros in 2022 by defeating Germany 2-1.

**METHODOLOGY**
Functions created for :-
 - to draw the pitch, 
 - extract passing data, 
 - dropping null values
 - separates location data to enable plotting
 - plotting completed vs imcomplete pass
 - separate to team and player passes

Using Kmeans, to identify the optimal number of clusters for meaningful analysis 

# Data Cleaning 

| Features Used     | Explanation                                           | Data Cleaning                                             |
|-------------------|-------------------------------------------------------|-----------------------------------------------------------|
| period            | first / second half                                   | -                                                         |
| location          | location of starting pass                             | in a form of [x,y] to loop over the rows and separate x,y |
| pass_end location | location of end pass                                  | as above                                                  |
| pass_outcome      | complete or incomplete                                | categorical data, get_dummies                             |
| pass_angle        | +ve indicates clockwise, -ve indicates anti clockwise | numerical data                                            |
| pass_height       | ground, low or high pass                              | categorical data, get_dummies                             |
| pass_length       | in yards                                              | numerical data                                            |

# Model Selection
I have chosen Kmeans clustering after running the cleaned data through Kmeans + PCA, and DBscan.
DBscan isn't a good clustering method to use because it classifies majority of the data as 1 big cluster and i wasn't able to gather any insights from the cluster.

# Team Analysis
Plotted percentage of completed passes over total passes for England over World Cup 19 and Euro 22. 84% passes completed in 2019 compared to 91% passes completed in 2022.

Through clustering, below are the findings:
Cluster 17 in World Cup 19 - signs of long balls from the goalie towards to right, recipient of these passes are the right full back (Lucy Bronze) + tallest England midfielder (Jill Scott). These passes are not seen in Euro 22 as the keeper plays short passes out from the back.

Passes made in zone 14 - in World Cup 19, Fran Kirby was the main passer and recipient in this area, which makes sense as she was the playmaker (no.10) in the team. more passes were seen reaching the goalmouth as well. In Euro 22, a change in tactical play is observed. Keira Walsh is the player most active in this area (25% of passes), but she plays holding midfielder for England, which is a position further behind the opposition goal.

Euro 22 : range of passing from defence
Leah Williamson, a left sided central defender, is seen higher up the pitch, contributing 35% of passes in cluster 17 (at the midfield line). Her positioning may explain how Keira has the capactiy to further push upfield to create chances.

# Player Analysis
Keira Walsh
339 passes made, 93% of passes completed in Euro 22 as compared to 265 passes made, 87% of passes completed in World Cup 19. This signals an improvement in passing. Progressive passes also increased, 156 passes made in World Cup 19 vs 193 passes made in Euro 22.

Through clustering of progressive passes, below are the findings:
Left sided passes (cluster 1, 34 passes in World Cup 19 vs cluster 0, 50 passes in Euro 22) 
Pass lengths were shorter on the left side back in 19, compared to longer ones in 22. This is very likely due to the speed of left wingers. In Euro 22, Lauren Hemp was running onto the left side pases, and she is one of the fastest wingers in this tournament.

Right sided long passes (cluster 2, 12 passes in World Cup 19 vs cluster 4, 26 passes in Euro 22) 
Consistency of long and high right sided passes seem to have improved, could be a mixture of better passing technique and presence of speedy right wingers in euro 22. In world cup 19, these passes were mainly made to right full back rather than a winger. 

Central passing in final third of the pitch (cluster 3, 29 passes in World Cup 19 vs cluster 2, 31 passes in Euro 22) 
Keira seems to be able to better progress her passes into the final third in Euro 22, as compared to 19. Let’s investigate further. 

Leah Williamson in Euro 22
462 passes made, 41% in offensive half
Comparing to 2 other defenders (Millie Bright and Marina Hegering) who have played the same number of games as Leah, she has made 1.5x more passes than the other 2, with 10% more passes landing in the offensive half. Based on her completed passes map, her passing range is equally good from left to right, compared to other defenders who are strong in only 1 side.

Through clustering of progressive passes, below are the findings:
Cluster 1 & 2 - 90 passes combined, located in the offensive half
28% of these passes go to Keira to allow her to utilise her passing range to get the ball to the wingers / forwards. The rest mostly go to attacking midfield, enabling England to launch attacks quicker.


---
## Conclusion 

Some key points on England’s Euro 22 success

A holding midfielder with a good passing technique is critical to the success of the team, as she is able to have attacking options from the back.

Keira’s technique have complemented well with fast wingers who can run onto passes. During transition play, this counter attack will generate lots of chances in the women’s game where defensive pressing styles is not prevalent in most teams, unlike the men’s game.

A defender who can push up forward and pass with precision, instead of just clearing balls and doing short and backward passes, will have a player advantage in midfield, allowing more players in attacking positions to create chances. 

On the flip side, this style of playing requires a high defensive line as Leah plays up to center line sometimes. This is susceptible to counter attacks if the other defender isn’t speedy or the defensive positioning isn’t good enough.


## Considerations
Opposition tactics need to be taken into account as explanation on why England play the way they do.

Data like through passes on goal, passing sequences leading to goal chances, can be incorporated into the clusters to understand where England’s goal threats and opportunities come from

--- 

### Notebook Contents
1. 01_Data Extraction & Cleaning
2. 02a_EDA & Modelling [Team Analysis WC19]
3. 02b_EDA & Modelling [Team Analysis Euro22]
4. 02c_EDA & Modelling [player analysis Keira Walsh wc19]
5. 02d_EDA & Modelling [player analysis Keira Walsh euro 22]
6. 02e_EDA & Modelling [player analysis Leah Williamson euro 22]
7. 03_KMeans + PCA & DBScan


---
