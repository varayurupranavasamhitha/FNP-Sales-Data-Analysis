# FNP Sales Data Analysis | MS Excel

Sales analysis of a Ferns and Petals (FNP) gifting dataset, built entirely in Microsoft Excel using Power Query, Power Pivot, Pivot Tables, Slicers, Timelines and formulas.

![Dashboard](dashboard.png)

## Dataset
Three tables from the FNP sample dataset (2023):
- **orders** (1,000 rows): customer, product, quantity, order and delivery date/time, delivery location, occasion
- **products** (70 rows): product name, category, price, occasion
- **customers** (100 rows): name, city, gender, contact details

*Note: this is a sample practice dataset, so the insights describe this data and not FNP's actual business.*

## Files
| File | Description |
|---|---|
| `Excel_sales_analysis_project_finall.xlsx` | Excel workbook with Power Query, Data Model, pivot tables, dashboard and analysis sheets |
| `orders.csv` | Order details |
| `products.csv` | Product details |
| `customers.csv` | Customer details |
| `Ferns and Petals Sales Analysis.pdf` | Problem statement with the 10 business questions |
| `dashboard.png` | Screenshot of the dashboard |

## What I did
**1. Data preparation (Power Query)**
- Loaded the three CSV files from a folder, promoted headers and set data types (dates, times, numbers, text).
- Added columns to orders: **Month Name** (from Order_Date), **diff_order_delivery** (Delivery_Date − Order_Date, in days) and **Hour** (from Delivery_Time).
- Merged orders with products on **Product_ID** to bring **Price (INR)** into the orders table.

**2. Data Model (Power Pivot)**
- Loaded all three tables into the Data Model, linked by Product_ID and Customer_ID.
- Created calculated columns: **Revenue** `= orders[Quantity] * orders[Price (INR)]` and **Day Name** of the order date.

**3. Interactive dashboard (Pivot Tables + Charts)**
- KPI cards: Total Orders, Total Revenue, Avg days between order and delivery, Avg order value.
- Pivot charts: Revenue by Occasions, Revenue by Category, Revenue by Months, Top 10 Cities by Orders, Top 5 Products by Revenue.
- Occasion slicer and Order Date / Delivery Date timelines for filtering.
- Additional charts: Peak vs Normal Months, % of Revenue by Customer Segment, Avg Delivery Days by Order Quantity, Top 5 Products - Monthly Revenue.

**4. Further analysis (Excel formulas)**
- **Peak Months:** monthly orders, revenue and delivery days using COUNTIFS, SUMIFS and AVERAGEIFS. Months with above-average orders are flagged as Peak.
- **Customer Segments:** customers ranked by total spend (SUMIF, RANK) and grouped into High (top 20), Mid (next 30) and Low (remaining 50).
- **What If:** effect on total revenue of increasing average order value in normal months.
- **Products and Delivery:** monthly revenue of the top 5 products (SUMIFS) and average delivery days by order quantity (COUNTIFS, AVERAGEIFS, CORREL).

## Key Insights
- Total revenue of ₹35.2L from 1,000 orders, with an average order value of ₹3,521 and an average delivery time of 5.5 days.
- Anniversary is the top occasion (₹6.7L) and Colors the top category (₹10.1L, 29% of revenue).
- 4 festival months (Feb, Mar, Aug, Nov), just 33% of the year, brought in 68% of revenue: Valentine's Day, Holi, Raksha Bandhan and Diwali.
- Peak months get about 4x more orders per month than normal months, while delivery time stays almost the same (5.6 vs 5.4 days).
- The top 20% of customers bring in 29% of revenue, so revenue is spread across many customers. High-value customers order more often rather than spending more per order.
- A 10% higher order value in normal months would add about 3.2% to total revenue.
- Dolores Gift sells only in August (Raksha Bandhan) and Harum Pack only in festival months, while Magnam Set and Deserunt Box sell throughout the year.
- Order quantity has no relationship with delivery time: 5.3 to 5.8 days for every quantity (CORREL ≈ 0).

## Data Notes
- Quia Gift appears under two Product IDs (21 and 56); both are added together in product totals.
- City in the Top 10 Cities chart is the customer's city from the customers table, not the order's delivery location.

## Recommendations
- Stock up and arrange extra delivery capacity 3–4 weeks before each festival.
- Use repeat-order / loyalty offers to increase how often customers order.

## Tools
Microsoft Excel: Power Query, Power Pivot (Data Model, DAX calculated columns), Pivot Tables, Pivot Charts, Slicers, Timelines, COUNTIFS, SUMIFS, AVERAGEIFS, SUMIF, RANK, CORREL.
