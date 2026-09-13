# 🚲 London Bike Demand Dynamics: Exploratory Data Analysis

A comprehensive, end-to-end Exploratory Data Analysis (EDA) of the London Bike Sharing system. This project investigates temporal usage patterns, environmental factors, and seasonal transitions to understand urban mobility dynamics, support business decision-making, and prepare features for predictive modeling.

---

## 📌 Project Overview & Objectives

* **Identify Core Usage Drivers:** Distinguish between commuter-driven demand (workdays) and leisure-driven usage (weekends/holidays).
* **Assess Environmental Impacts:** Evaluate the effect of temperature, humidity, wind speed, and weather conditions on rental volumes.
* **Detect Anomaly Patterns:** Pinpoint single-day volume spikes (e.g., transit strikes) and long-term macro trends.
* **ML Model Preparation:** Uncover feature relationships and multicollinearity to guide future feature engineering and predictive modeling.

---

## 📊 Dataset & Feature Glossary

The dataset covers hourly bike rental records in London alongside calendar and environmental variables.

| Feature Name | Data Type | Description |
| :--- | :--- | :--- |
| **`timestamp`** | Datetime | Timestamp field for grouping and time-series aggregation |
| **`cnt`** | Integer | Total count of new bike shares **(Target Variable)** |
| **`t1`** | Float | Real temperature in Celsius (°C) |
| **`t2`** | Float | "Feels like" temperature in Celsius (°C) |
| **`hum`** | Float | Relative air humidity percentage (%) |
| **`wind_speed`** | Float | Wind speed in km/h |
| **`weather_code`** | Categorical | Categorical code representing current weather conditions |
| **`is_holiday`** | Boolean | `1` = Public Holiday, `0` = Non-Holiday |
| **`is_weekend`** | Boolean | `1` = Weekend, `0` = Weekday |
| **`season`** | Categorical | Meteorological season: `0` = Spring, `1` = Summer, `2` = Fall, `3` = Winter |

### 🌤️ Weather Code Reference (`weather_code`)

* `1`: Clear / Mostly Clear *(includes haze / fog patches)*
* `2`: Scattered Clouds / Few Clouds
* `3`: Broken Clouds
* `4`: Cloudy
* `7`: Rain / Light Rain Shower
* `10`: Rain with Thunderstorm
* `26`: Snowfall
* `94`: Freezing Fog

---

## 🔍 Key Findings & EDA Insights

### 1. Commuter Dominance & Behavioral Patterns
* **Weekday vs. Weekend Share:** Weekdays represent **75.6% (15.05M)** of overall rental volume, whereas weekends account for **24.4% (4.86M)**.
* **Bimodal Commuting Peaks:** Workdays exhibit sharp peaks at **08:00** and **17:00–18:00**, confirming that daily commutes form the backbone of the system.
* **Leisure Shift:** On weekends and public holidays, commuter spikes disappear into a broad, unimodal afternoon curve peaking between **12:00 and 16:00**.

### 2. Environmental & Seasonal Correlations
* **Temperature Effect:** Real temperature (`t1`, r = +0.39) and feels-like temperature (`t2`, r = +0.37) share moderate positive correlations with rental demand.
* **Humidity Deterrent:** Humidity (`hum`, r = -0.46) shows the strongest inverse relationship with bike rentals.
* **Multicollinearity:** `t1` and `t2` are highly collinear (~0.99). Retain `t1` and consider dropping `t2` for predictive modeling.

### 3. Historical Anomalies & Macro Trends
* **Single-Day Historical Peak:** The absolute maximum daily rental volume occurred on **July 9, 2015 (72,504 rentals)** due to a major London Underground public transport strike.
* **Monthly Peak:** **July 2016** recorded the highest cumulative monthly volume across the entire dataset, driven by summer seasonality.

---

## 💡 Strategic Business Recommendations

1. 🛠️ **Fleet Rebalancing & Maintenance:** Schedule routine fleet maintenance during Winter months and weekend off-peak hours. Prioritize rebalancing efforts at major transit hubs before **08:00** and **17:00** on weekdays.
2. 🚨 **Transit Contingency Planning:** Policies can be established to deploy emergency bike capacity during public transport disruptions or tube strikes.
3. 📈 **Demand Stimulation:** Implement targeted promotions during high-humidity days and Winter months to stabilize baseline rental activity.

---

## 🛠️ Tech Stack & Dependencies

* **Language:** Python
* **Data Manipulation:** `pandas`, `numpy`
* **Data Visualization:** `matplotlib`, `seaborn`
