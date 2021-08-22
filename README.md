# Surf's Up with SQLite
## I. Overview of Project

### Background

I have been planning to open Surfing Shake Shop in Hawaii, serving surfboards and ice cream to locals and tourists. My investor, W. Avy, is very supportive to the plan, but he has one concern: the weather. Weather is going to be a serious factor because it directly affects the surfing business. For this project, I have run some analytics on a weather dataset of the island to determine the weather trend and the business potential.

### Purpose
The purpose of this challenge is to:

1.	Determine the summary statistics for June temperature.
2.	Determine the summary statistics for December temperature.
3.	Analysis the key differences in weather between June and December.
4.	Write two additional queries to gather more weather data for June and December.

## II. Results

![junedecember](https://user-images.githubusercontent.com/84211948/130351433-160924e4-62f1-4a5c-9a38-0513d4c66a32.png)

1.	The minimum temperature is 64°F in June and is 56°F in December. June’s minimum temperature is 8°F higher than December’s minimum temperature.
2.	The max temperature is 85°F in June and is 83°F in December. June’s max temperature 2°F higher than December’s max temperature.
3.	The average temperature is 74.94°F in June and is 71.04°F in December. June is about 4°F higher than December.
4.	Lower, middle and upper quartiles in June are all about 3-4°F higher than in December.

## III. Summary

From the summary statistics tables and results above we can conclude that June is generally slightly hotter than December. However, the difference is quite small: 4°F difference in average temperature. Both June and December are very suitable for surfing and ice cream in terms of temperature. 

However, temperature is not the only weather factor to determine the potential for surfing, precipitation is also extremely important. For high level surfers, slightly lower temperatures don’t stop them from surfing, but precipitation does. Heavy rains may cause serious safety concerns, especially that ocean is very unpredictable. Therefore, to get more weather data from June and December for further analysis, I created another two additional queries to retrieve June’s and December’s precipitation.

### Additional Queries and Tables

#### 1. June Precipitation

1.1 Write a query that filters the Measurement table to retrieve the precipatation for the month of June.

```june_prcp = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 6)```

1.2 Convert the June precipatation to a list.

```june_prcp_list = [prcp.prcp for prcp in june_prcp]```

1.3 Create a DataFrame from the list of precipitation for the month of June. 

```june_prcp_df = pd.DataFrame(june_prcp_list, columns=["precipitation"])```

1.4 Calculate and print out the summary statistics for the June precipitation DataFrame.

```june_prcp_df.describe()```

#### 2.	December Precipitation

2.1 Write a query that filters the Measurement table to retrieve the precipatation for the month of December.

```december_prcp = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 12)```

2.2 Convert the December precipatation to a list.

```december_prcp_list = [prcp.prcp for prcp in december_prcp]```

2.3 Create a DataFrame from the list of precipitation for the month of December. 

```december_prcp_df = pd.DataFrame(december_prcp_list, columns=["precipitation"])```

2.4 Calculate and print out the summary statistics for the June precipitation DataFrame.

```december_prcp_df.describe()```

#### 3. Precipitation Results

![junedecemprpc](https://user-images.githubusercontent.com/84211948/130352019-43672b8b-a2cd-404e-9b30-4c0f07bd4924.png)

June's average precipitation is 37.1% lower than December's precipitation. June's max and upper quartile precipitation are also both higher than December's. In conclusion, June's weather is more capable for surfing. With previous conclusion that June's temperture is higher, we can predict that June's surfing and ice cream business should be better.
