# Superstore Sales Analysis: Power BI Dashboard

An interactive, Power BI report that analyses Superstore sales, profit, products, shipping operations and customers analysis.


---


## Project Overview

This project turns the Superstore sales dataset into a decision-support report. It lets a sales manager, operations lead or sales analyst to:

- Track headline KPIs (sales, profit, orders, customers, growth, margin)
- See which regions, states, categories and products drive or hurt profit
- Monitor shipping performance and order returns
- Understand the customer base by segment, payment mode and geography


## Business Questions Answered


| Area | Question |
|------|----------|
| Sales | How are sales trending month by month and year over year? |
| Profitability | Which categories, sub-categories and products make or lose money? |
| Geography | Which regions and states perform best? |
| Operations | How long does shipping take, and which ship modes are used most? |
| Returns | What share of orders is returned, and which ship modes see the most returns? |
| Customers | Where are customers located, and how do segments and payment modes split? |

---

## Report Pages

### 1. Executive Sales Overview
High-level summary of business performance.

- **KPI cards:** Total Orders, Total Profit, Total Sales, Total Customers, YoY Sales Growth %, Profit Percentage %, Average Order Value
- **Line chart:** Total Sales by Year and Month
- **Donut chart:** Total Sales by Category
- **Bar chart:** Total Sales by Region
- **Column chart:** Total Profit by Category
- **Map:** *Geographic Sales Performance* by State (bubble size = Total Sales; tooltips show Sales, Profit, Orders)

### 2. Product Analysis
Which products and categories create (or destroy) value.

- **Bar charts:** Sales by Sub-Category; Total Profit by Sub-Category
- **Column chart:** *Top 10 Products by Sales*
- **Bar chart:** *Top 10 Products by Profit*
- **Donut chart:** Sales by Segment
- **Column chart:** Sales by Payment Mode
- **Table:** *Loss-Making Products* (Profit, Sales, Profit Margin %)
- **Table:** *Profit by Category* (Sales, Profit, Profit Margin %)

### 3. Operations & Shipping
Fulfilment speed, ship-mode mix and returns.

- **KPI cards:** Total Orders, Returned Orders, Return Rate %, Total Quantity, Avg Shipping Days
- **Column chart:** Total Orders by Ship Mode
- **Donut charts:** Orders by Return Status; Returned Orders by Ship Mode
- **Bar chart:** Avg Shipping Days by Ship Date (Year and Month)
- **Clustered bar chart:** Profit by Ship Mode, split by Region
- **Table:** *Orders by Region* (Orders, Profit, Sales)

### 4. Customer Analysis
Who the customers are and where they are.

- **Column chart:** Customer count by Return Status
- **Donut chart:** *Return Status* share of customers
- **Treemap:** Customer count by State
- **Clustered bar chart:** *Count of Customer by Payment Mode and Segment*
- **Map:** Customer count by State

---

## Data Model

The model contains three tables:

| Table | Role |
|-------|------|
| `SuperStore_Sales_Dataset (2)` | Fact/transaction table with one row per order line |
| `Calendar` | Date table used for Year/Month analysis and time intelligence |
| `Table` | Holds the report's DAX measures |


**Fields used from the sales table** (as seen in report visuals):
`Category`, `Sub-Category`, `Product Name`, `Segment`, `Region`, `State`, `Customer ID`, `Ship Mode`, `Payment Mode`, `Return Status`, `Ship Date`, `Sales`, `Profit`

**Calendar table fields used:** `Date` (with Year/Month hierarchy), `Year`

--------

## DAX Measures

The following measures are used in the report. They live in the `Table` measure table.

| Measure | Used on | Purpose |
|---------|---------|---------|
| Total Sales | All pages | Sum of sales |
| Total Profit | Overview, Product | Sum of profit |
| Total Orders | Overview, Operations | Count of orders |
| Total Customers | Overview | Count of distinct customers |
| Total Quantity | Operations | Sum of units sold |
| YoY Sales Growth % | Overview | Year-over-year change in sales |
| Profit Percentage % | Overview | Profit as a percentage of sales |
| Profit Margin % | Product | Profit Ã· Sales at category/product level |
| Average Order Value | Overview | Sales Ã· Orders |
| Returned Orders | Operations | Number of returned orders |
| Return Rate % | Operations | Returned Orders Ã· Total Orders |
| Avg Shipping Days | Operations | Average days between order and ship date |
| Orders by Status | Operations | Orders split by Return Status |


---

## Filters and Interactivity

Every page has the same slicer panel, so filters stay consistent across the report:

- Year
- Category
- Sub-Category
- Region
- Segment
- Ship Mode
- Payment Mode

All visuals cross-filter each other. Clicking a bar, slice or map region filters the rest of the page. The Overview map has tooltips with Sales, Profit and Orders.

---




## Key Insights



- **Sales trend:** e.g. "Sales grew X% YoY, with peaks in November and December."
- **Top region/state:** e.g. "The West region leads sales; California is the top state."
- **Most profitable category:** e.g. "Technology has the highest margin at X%."
- **Loss-makers:** e.g. "N products sell at a loss; the largest losses are in Tables and Bookcases."
- **Shipping:** e.g. "Standard Class is the most used ship mode; average shipping time is X days."
- **Returns:** e.g. "The return rate is X%, highest for ship mode Y."

---


 

