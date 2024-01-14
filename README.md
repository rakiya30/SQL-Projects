## SQL-Project
# Super Store Sales Analysis

-- Overview of Superstore--

SELECT COUNT (order_id) AS Total_orders,

COUNT(DISTINCT country) AS Total_countries,

COUNT(DISTINCT category) AS Total_categories,

COUNT(DISTINCT year) AS Total_years,
SUM(sales) AS Total_sales, 

SUM(quantity) AS Total_quantity_sold,

AVG(profit) AS Average_profit,

AVG(discount) AS Average_discount

FROM super_store.dbo.SuperStoreOrders

-- Sales Performance Analysis--

SELECT TOP 10

product_name,

category,

SUM(sales) AS Total_sales,

SUM(quantity) AS Total_quantity_sold

FROM super_store.dbo.SuperStoreOrders

GROUP BY

product_name,

category

ORDER BY

SUM(sales) DESC

-- Sales over Year--

SELECT

year,

SUM(sales) AS Total_sales

FROM super_store.dbo.SuperStoreOrders

GROUP BY year

ORDER BY SUM(sales) DESC

-- Customer Segmentation--

SELECT

segment,

COUNT(DISTINCT customer_name) AS Total_customers,

SUM(sales) AS Total_sales


FROM super_store.dbo.SuperStoreOrders

GROUP BY segment

ORDER BY SUM(sales) DESC

-- Shipping and Management Orders--

SELECT

ship_mode,

AVG(shipping_cost) AS avg_shipping_cost,

AVG(profit) AS avg_profit

FROM super_store.dbo.SuperStoreOrders

GROUP BY ship_mode

ORDER BY AVG(profit) 

-- Time Analysis--

SELECT

ship_mode,

AVG(DATEDIFF(day, order_date, ship_date)) AS avg_time_gap

FROM super_store.dbo.SuperStoreOrders

GROUP BY ship_mode

-- Profitability and Cost Analysis---

SELECT

product_name,

category,

sub_category,

AVG(profit) AS avg_profit,

AVG(discount) AS avg_discount

FROM super_store.dbo.SuperStoreOrders

GROUP BY

product_name,

category,

sub_category

ORDER BY AVG(profit) DESC

-- Global Sales and Quantity Overview--

SELECT

country,

SUM(sales) AS Total_sales,

SUM(quantity) AS Total_quantity_sold

FROM super_store.dbo.SuperStoreOrders

GROUP BY country

ORDER BY SUM(sales) DESC

-- State Level Category Exploration--

SELECT

product_name,

category,

SUM(quantity) AS Total_quantity_sold

FROM super_store.dbo.SuperStoreOrders

GROUP BY product_name,

category

ORDER BY SUM(quantity) DESC


--Regional Sub-category Analysis--

SELECT 

region,

sub_category,

SUM(quantity) AS Total_quantity_sold

FROM super_store.dbo.SuperStoreOrders

GROUP BY region,

sub_category

ORDER BY SUM(quantity) DESC


ALTER TABLE super_store.dbo.SuperStoreOrders
ALTER COLUMN product_name nvarchar(max)
GO


