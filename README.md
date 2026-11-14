Datheon Data Analytics & Power BI Internship

Projects completed during the Data Analytics & Power BI Internship at Datheon (virtual, project-based, Nov 2026).

Intern: Zakiya Sharieff, MCA, CMR University GitHub: zakiya-dev

Projects
Task	Project	Tools	Status
1	Exploratory Data Analysis on Superstore Retail Sales	Python, Pandas, Matplotlib, Seaborn, Jupyter	Completed
2	Interactive Power BI Executive Sales & Profit Dashboard	Power BI Desktop, DAX, Power Query	Completed
Task 1: Superstore Retail Sales EDA

Goal: Clean the Superstore sales data, profile missing values, and find insights on customer purchase volume, monthly seasonality, category-wise revenue and discount sensitivity.

Notebook: Task1_Superstore_EDA.ipynb Cleaned data: superstore_cleaned.csv Charts: figures/

Data cleaning
The raw file had 10,800 rows, but only 9,994 are real orders. The last 806 rows were two lookup tables pasted below the data (regional managers and a list of returned orders). I separated them and kept the returns as a Returned flag.
The only missing values were 11 postal codes, all for Burlington, Vermont. They were filled in, and they are not used in any calculation.
Converted date columns (month/day/year) to proper dates, stored postal codes as text to keep leading zeros, and checked for duplicates, invalid dates, and non-positive sales or quantities (none found).
Added features: year, month, year-month, shipping days, profit margin %, returned flag and discount bands.
Key findings
Sales are growing and margin is improving. Sales rose from about $484K (2015) to $733K (2018), up 51%, and profit nearly doubled.
Sales are strongly seasonal. September, November and December are the peak months. November and December alone bring in about 30% of annual sales, while January and February are the weakest.
Furniture sells a lot but earns almost nothing. It generates about $742K in sales but only about $18K in profit (about 2.5% margin), far below Technology and Office Supplies.
Heavy discounting destroys profit. Items with no discount earn a 29.5% margin. Above a 20% discount, margins turn negative, and those lines lost a combined $135K.
A few sub-categories lose money. Tables (about -$17.7K), Bookcases (about -$3.5K) and Supplies (about -$1.2K) are loss-making overall.
Regional performance is uneven. West and East lead, while Central has the weakest margin (about 8% vs about 15% in West).
The customer base is broad. 793 customers place about 6 orders each on average, and the top 10 account for only about 7% of sales.
Returns are modest. About 6% of orders (296 of 5,009) were returned, with a similar share across all three categories.
Selected charts
	
Yearly sales and profit	Monthly seasonality
Category performance	Profit by sub-category
Discount vs profit	Margin by discount band
How to run
bash
pip install pandas matplotlib seaborn notebook

Open Task1_Superstore_EDA.ipynb in Jupyter or VS Code. Place superstore_sales.csv (the original dataset) in the same folder and run all cells. The notebook generates superstore_cleaned.csv and the charts in figures/.

Task 2: Power BI Executive Sales & Profit Dashboard

Goal: Turn the cleaned Superstore data into an interactive, multi-page executive dashboard in Power BI Desktop.

Files: Task2_Superstore_Dashboard.pbix · Task2_Superstore_Dashboard.pdf · screenshots/

Data model
Used the cleaned dataset from Task 1 (superstore_cleaned.csv) as the source.
Built a star schema in Power Query: one fact table (Fact_Orders) and dimension tables for customers (Dim_Customer) and products (Dim_Product), plus a calendar table (Dim_Date, created with DAX and marked as the date table).
Relationships are many-to-one with single-direction filtering, connected through Order Date, Customer ID and Product ID.
DAX measures

Total Sales, Total Profit, Profit Margin % (DIVIDE([Total Profit], [Total Sales], 0)), Total Orders, Avg Order Value, Avg Discount %, Return Rate %, Sales LY, YoY Sales Growth %, Profit LY and YoY Profit Growth %.

Dashboard pages

1. Executive Overview: KPI cards (sales, profit, margin, orders, YoY sales growth and YoY profit growth), year and region slicers, a monthly sales trend line, and a category and sub-category treemap.

Executive Overview

2. Product Profitability: a sub-category by region profit margin matrix with red-to-green conditional formatting, profit by sub-category, and a scatter plot of average discount against profit margin.

Product Profitability

3. Regions & Customers: sales and profit by region, a regional treemap, sales by customer segment, the top 10 customers (Top N filter) and the return rate.

Regions and Customers

Insights (2018 view)
Sales reached $733K and profit $93K (12.7% margin), with 20.4% sales growth and 14.2% profit growth over 2017.
Tables, Machines, Supplies and Bookcases are loss-making in 2018, and the scatter plot shows that the sub-categories with the highest average discounts earn the lowest margins.
Central has the lowest regional margin (5.1%), against 17.5% in West.
Revenue is spread across many customers: the top 10 account for about 12% of 2018 sales.

The dashboard is set to 2018, and the Year slicer lets you view any year from 2015 to 2018. YoY measures are blank for 2015, as there is no 2014 data.

Repository structure
Datheon_DataAnalytics_Internship/
├── README.md
├── Task1_Superstore_EDA/
│   ├── Task1_Superstore_EDA.ipynb
│   ├── superstore_cleaned.csv
│   └── figures/
└── Task2_PowerBI_Dashboard/
    ├── Task2_Superstore_Dashboard.pbix
    ├── Task2_Superstore_Dashboard.pdf
    └── screenshots/
Tech stack

Python · Pandas · Matplotlib · Seaborn · Jupyter · Power BI · DAX · Power Query · Git/GitHub
