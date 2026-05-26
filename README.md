<div align="center">

<h1>🛍️ Retail Customer Behavior & Revenue Insights</h1>

<p><strong>End-to-End Data Analytics Project · Python · SQL · Power BI</strong></p>

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-22c55e?style=for-the-badge)

<br/>

> **Analyzed 3,900 retail transactions to uncover customer segments, revenue drivers, and discount dependency patterns — delivering actionable business intelligence through Python, SQL, and Power BI.**

</div>

---

## 📌 Project Overview

This is a **corporate-grade, end-to-end data analytics project** that simulates the real responsibilities of a professional data analyst — from raw data to boardroom-ready insights.

The dataset contains **3,900 retail transactions** across **18 features**, covering customer demographics, purchase behavior, shipping preferences, review ratings, and discount usage.

**Business questions answered:**
- Which customer segments drive the most revenue?
- How loyal is the customer base — and who are the repeat buyers?
- Which products are over-reliant on discounts?
- How do subscribers compare to non-subscribers in spend?
- What does KPI health look like across age groups, categories, and shipping types?

---

## 📊 Key Results at a Glance

| Metric | Value |
|--------|-------|
| 🧾 Total Transactions | 3,900 |
| 👥 Total Customers | 3,900 |
| 💰 Avg Purchase Value | $59.76 |
| ⭐ Avg Review Rating | 3.75 / 5 |
| 🏆 Top Revenue Segment | Young Adults — $62,143 |
| 💛 Loyal Customers | 3,116 (≈80%) |
| 🏷️ Highest Discount Dependency | Hat (50%), Sneakers (49.66%), Coat (49.07%) |
| 🚀 Subscribers | 1,053 (27%) vs 2,847 Non-Subscribers |

---

## 🗂️ Project Workflow

```
Raw CSV Data
     │
     ▼
┌─────────────────────┐
│  Python (Pandas)    │  ── Clean, engineer features, load to DB
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│  PostgreSQL (SQL)   │  ── 10 business queries: CTEs, Window Functions, Subqueries
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│  Power BI           │  ── Interactive dashboard with KPI cards + slicers
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│  Report + Deck      │  ── Business recommendations for stakeholders
└─────────────────────┘
```

---

## 📂 Repository Structure

```
📦 retail-customer-behavior-analysis
 ┣ 📓 Customer_Shopping_Behavior_Analysis.ipynb   ← Python: EDA + Cleaning + DB Load
 ┣ 🗃️ customer_behavior_sql_queries.sql            ← SQL: 10 Business Queries
 ┣ 📊 customer_behavior_dashboard.pbix             ← Power BI Dashboard
 ┣ 📄 Project_Report.pdf                           ← Final Report
 ┗ 📁 data/
    ┗ raw_data.csv
```

---

## 🛠️ Tech Stack

| Layer | Tool | What was done |
|-------|------|---------------|
| Data Wrangling | Python (Pandas) | Cleaning, imputation, feature engineering |
| Database | PostgreSQL | Data storage + SQL analysis |
| Visualization | Power BI | Interactive KPI dashboard |
| Reporting | PDF / Gamma AI | Stakeholder report & presentation |

---

## ⚙️ Step 1 — Data Preparation & EDA (Python)

**Dataset shape:** 3,900 rows × 18 columns

**Cleaning steps performed:**

| Step | Action |
|------|--------|
| Missing Data | 37 null values in `review_rating` — imputed using **median per product category** |
| Column Standardization | Renamed all columns to `snake_case` |
| Redundancy Check | `discount_applied` and `promo_code_used` were redundant → dropped `promo_code_used` |
| Feature Engineering | Created `age_group` (binned ages) and `purchase_frequency_days` |
| DB Integration | Loaded cleaned DataFrame into PostgreSQL via SQLAlchemy |

**Dataset overview (describe output):**

| Stat | Customer ID | Age | Purchase Amount (USD) | Review Rating |
|------|-------------|-----|-----------------------|---------------|
| count | 3900 | 3900 | 3900 | 3863 |
| mean | 1950.5 | 44.07 | $59.76 | 3.75 |
| std | 1125.98 | 15.21 | $23.69 | 0.72 |
| min | 1 | 18 | $20 | 2.5 |
| max | 3900 | 70 | $100 | 5.0 |

```bash
# Clone the repo
git clone https://github.com/tinayerne04/retail-customer-behavior-analysis.git
cd retail-customer-behavior-analysis

# Install dependencies
pip install pandas sqlalchemy psycopg2 jupyter matplotlib seaborn

# Run the notebook
jupyter notebook Customer_Shopping_Behavior_Analysis.ipynb
```

---

## 🗃️ Step 2 — SQL Analysis (PostgreSQL)

10 business queries using **CTEs**, **Window Functions**, and **Subqueries**.

### Query 1 · Revenue by Gender

| Gender | Revenue |
|--------|---------|
| Male | $157,890 |
| Female | $75,191 |

### Query 2 · High-Spending Discount Users
> Customers who used discounts but still spent **above average purchase amount**

- **839 customers** qualified
- Proves discounts don't always reduce basket size — a strong upsell opportunity

### Query 3 · Top 5 Products by Avg Review Rating

| Rank | Product | Avg Rating |
|------|---------|------------|
| 1 | Gloves | 3.86 |
| 2 | Sandals | 3.84 |
| 3 | Boots | 3.82 |
| 4 | Hat | 3.80 |
| 5 | Skirt | 3.78 |

### Query 4 · Shipping Type vs Avg Purchase Amount

| Shipping Type | Avg Purchase |
|---------------|-------------|
| Express | $60.48 |
| Standard | $58.46 |

> Express shipping customers spend slightly more — indicator of higher purchase intent.

### Query 5 · Subscribers vs Non-Subscribers

| Subscription | Customers | Avg Spend | Total Revenue |
|-------------|-----------|-----------|---------------|
| Yes | 1,053 | $59.49 | $62,645 |
| No | 2,847 | $59.87 | $170,436 |

> Subscription conversion is only **27%** — major growth lever untapped.

### Query 6 · Discount-Dependent Products

| Product | Discount Rate |
|---------|--------------|
| Hat | 50.00% |
| Sneakers | 49.66% |
| Coat | 49.07% |
| Sweater | 48.17% |
| Pants | 47.37% |

> These 5 items are priced or positioned to **require** discounts to move — margin risk.

### Query 7 · Customer Segmentation

| Segment | Count |
|---------|-------|
| Loyal | 3,116 |
| Returning | 701 |
| New | 83 |

> **80% of the base is Loyal** — strong retention. Focus should shift to basket growth, not acquisition.

### Query 8 · Top 3 Products per Category (Window Function)

| Category | #1 | #2 | #3 |
|----------|----|----|-----|
| Accessories | Jewelry (171) | Sunglasses (161) | Belt (161) |
| Clothing | Blouse (171) | Pants (171) | Shirt (169) |
| Footwear | Sandals (160) | Shoes (150) | Sneakers (145) |
| Outerwear | Jacket (163) | Coat (161) | — |

### Query 9 · Repeat Buyers & Subscriptions

| Subscription | Repeat Buyers (>5 purchases) |
|-------------|------------------------------|
| No | 2,518 |
| Yes | 958 |

> Heavy buyers are **not subscribing** — subscription incentives need to target this segment directly.

### Query 10 · Revenue by Age Group

| Age Group | Total Revenue |
|-----------|--------------|
| Young Adult | $62,143 |
| Middle-aged | $59,197 |
| Adult | $55,978 |
| Senior | $55,763 |

---

## 📊 Step 3 — Power BI Dashboard

**KPI Cards:**

| KPI | Value |
|-----|-------|
| Number of Customers | 3.9K |
| Average Purchase Amount | $59.76 |
| Average Review Rating | 3.75 |

**Dashboard features:**
- Subscription status breakdown: **Yes 27% / No 73%** (donut chart)
- Revenue by Category and Age Group (bar charts)
- Sales by Category and Age Group
- **Slicers:** Gender, Category, Subscription Status, Shipping Type

**Setup:**
```
1. Open customer_behavior_dashboard.pbix in Power BI Desktop
2. Update PostgreSQL connection → your local credentials
3. Click Refresh
```

---

## 💡 Business Recommendations

| # | Finding | Recommendation |
|---|---------|----------------|
| 1 | Only 27% subscribed, but avg spend is near-equal | Launch exclusive subscriber perks to convert the 73% |
| 2 | 3,116 Loyal customers (80%) | Shift spend from acquisition → upsell & basket size growth |
| 3 | Hat, Sneakers, Coat at ~50% discount rate | Audit pricing — reduce discount dependency, protect margins |
| 4 | Top-rated: Gloves, Sandals, Boots | Feature these in paid campaigns — social proof sells |
| 5 | Young Adults = $62,143 top revenue | Prioritize this segment in targeting, content, and promotions |
| 6 | 2,518 repeat buyers not subscribed | Trigger subscription prompts after 3rd purchase |

---

## 🚀 How to Run

```bash
# 1. Clone
git clone https://github.com/tinayerne04/retail-customer-behavior-analysis.git

# 2. Dependencies
pip install pandas sqlalchemy psycopg2 jupyter matplotlib seaborn

# 3. Python notebook — cleaning, EDA, DB load
jupyter notebook Customer_Shopping_Behavior_Analysis.ipynb

# 4. SQL — run in PostgreSQL client
# Open: customer_behavior_sql_queries.sql

# 5. Power BI — open .pbix and refresh data source
```

---

## 📜 License

MIT — Free to fork ⭐ and use in your own portfolio.

---

## 👩‍💻 About

**Tina Yerne** — Aspiring Data Analyst. Turning raw data into clear business decisions.

[![GitHub](https://img.shields.io/badge/GitHub-tinayerne04-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/tinayerne04)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Tina%20Yerne-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/tina-yerne-32645a24b/)

---

<div align="center">
<strong>If this helped you, drop a ⭐ — it means a lot!</strong><br/>
<em>Built with Python · PostgreSQL · Power BI</em>
</div>
