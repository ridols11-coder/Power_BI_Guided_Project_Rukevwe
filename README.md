# Hotel Booking Performance (2018-2020)
## 🏨 Business Problem
Between 2018 and 2020, the hotel experienced fluctuations in bookings and revenue, but the underlying factors driving these changes remain unclear. The management team seeks a comprehensive understanding of the hotel’s performance across this three-year period to make data-informed strategic decisions. Specifically, there is a need to analyze booking patterns, revenue trends, and customer behavior to identify which market segments, booking channels, and customer types contribute most to the hotel’s growth, and which areas present opportunities for improvement.

The objective of this analysis is to evaluate the hotel’s overall booking and revenue performance from 2018 to 2020, uncovering patterns that reveal customer preferences, high-performing segments, and underperforming areas. By examining key performance indicators—such as total bookings, total revenue, and booking ratios—alongside breakdowns by customer type, market segment, country, and meal type, the hotel aims to gain actionable insights that will support decisions to optimize marketing strategies, improve customer retention, and maximize revenue potential.

## 🗂️ Dataset Information

The dataset used for this project contains hotel booking records collected between 2018 and 2020. It provides a detailed view of customer reservations, including booking sources, customer demographics, stay durations, and revenue metrics.

This dataset serves as the foundation for understanding hotel performance, enabling analysis of booking trends, revenue growth, and customer preferences over time.

## 📁 Source

The data is derived from publicly available hotel booking datasets and has been prepared for analytical use. It includes records from both City Hotels and Resort Hotels.

## 🧹 Data Preparation Steps
- Removed null and duplicate records.
- Replaced binary values (e.g., is_canceled) with descriptive labels (“Canceled” / “Not Canceled”).
- Converted date fields into year and month formats for time-series analysis.
- Created calculated measures for key performance indicators (e.g., Total Revenue, Booking Ratio, Average Daily Rate).

## Preprocess the dataset
  Before analysis, the dataset was thoroughly cleaned and transformed in Power Query to ensure consistency, accuracy, and usability for dashboard visualization. The preprocessing steps focused on removing errors, standardizing formats, and creating meaningful calculated columns and measures to support insights generation.

🔧 Steps Performed

1. Data Importation

- Loaded multiple yearly datasets (2018–2020) into Power Query.

- Used the Append Queries function to combine them into one master dataset for analysis.

2. Data Cleaning

- Removed duplicate records and irrelevant columns (e.g., internal reference codes).

- Replaced missing or null values with appropriate defaults (e.g., 0 for numeric fields, “Unknown” for categorical).

- Verified data types — ensuring columns like adr, lead_time, and stays_in_week_nights were in numeric format, while country and meal were set to text.

3. Data Transformation

- Standardized categorical values:

Replaced binary codes in is_canceled with readable labels:
1 → "Canceled", 0 → "Not Canceled".

Normalized meal types: SC → No Meal, BB → Bed & Breakfast, HB → Half Board, FB → Full Board.

Created derived columns such as:

- Total Nights = stays_in_week_nights + stays_in_weekend_nights

- Total Guests = adults + children + babies

- Revenue = adr × Total Nights

4. Data Filtering

- Removed records with adr ≤ 0 or unrealistic stay lengths.

5. Feature Engineering

- Extracted Month and Year from date fields for time-based analysis.

- Created calculated measures in Power BI:

Total Revenue = SUMX(Hotel_Data, Hotel_Data[Revenue])

Booking Ratio = COUNT(Bookings) / COUNT(Total Possible Bookings)

6. Validation

- Cross-checked totals and averages against raw data exports.

- Ensured consistency in customer segment and market channel classifications.

## 🧾 Outcome

After preprocessing:

The dataset was clean, structured, and analysis-ready.

All key metrics could be accurately visualized and aggregated across years, customer types, and market segments.

The final dataset was used to power an interactive Power BI dashboard for hotel performance insights.
# 📊 Visualization and Charts
To better understand booking patterns, customer behavior, and revenue performance, a series of interactive visualizations were created in Power BI.
These visuals help management quickly identify trends, outliers, and key growth drivers between 2018 and 2020.

<img width="580" height="332" alt="image" src="https://github.com/user-attachments/assets/f934467a-2767-4281-adbf-191ad3af5ec2" />
<img width="589" height="336" alt="image" src="https://github.com/user-attachments/assets/a25c2485-90b4-4de2-9456-888628316ebc" />

## Data Modelling and Relationship
The data model was designed using a star schema, where the central fact table — Hotel_Data — connects to several dimension tables that provide descriptive context. This structure enables efficient querying, aggregation, and dashboard creation in Power BI. The Hotel_Data table serves as the core fact table that stores transactional details of each hotel booking.

## Model Type:

Schema: Star Schema

Relationship Type: One-to-Many (1→*)

Cross Filter Direction: Single

Primary Keys: Each dimension table has a unique identifier used to connect to the fact table.
<img width="735" height="362" alt="image" src="https://github.com/user-attachments/assets/3e2846b0-d2b8-4390-9921-41e25b033286" /> 

