# Online Retail — Exploratory Data Analysis

## Project Scenario

A UK-based online retailer wants to understand its transactional data to make
better commercial decisions: which products drive sales, which markets and
customers matter most, and when demand peaks during the year. The raw data,
however, is messy — it contains duplicate rows, missing customer identifiers,
and invalid (negative) quantities and prices from cancellations and returns.

This project takes that raw transactional data (`Online Retail.xlsx`), cleans
it, and explores it to surface the insights the business needs.

## Skills Demonstrated

- **Data cleaning & preparation** — removing duplicates, handling missing
  values, and separating cancellations/returns from genuine sales.
- **Feature engineering** — deriving `Year`, `Month`, `Day of Week`, and
  `Revenue` columns from raw transaction fields.
- **Exploratory data analysis** — using groupby aggregations to rank products,
  customers, countries, and time periods.
- **Statistical testing** — Shapiro-Wilk normality tests on `Quantity` and
  `UnitPrice`, and a Pearson correlation between month and units sold.
- **Data visualization** — communicating findings with clear bar charts,
  boxplots, and a regression/trend plot.
- **Reusable, function-driven code** — encapsulating cleaning and plotting
  logic into functions (`clean_data`, `plot_top_products`, `print_info`).

## Tools Used

- **Python 3**
- **pandas** — data loading, cleaning, and aggregation
- **NumPy** — numeric operations
- **Matplotlib** & **seaborn** — visualization
- **SciPy** — statistical tests (Shapiro-Wilk normality, Pearson correlation)
- **openpyxl** — reading the Excel source file
- **Jupyter Notebook** — interactive analysis environment

## Summary

The analysis transforms a raw retail transaction log into a set of actionable
business insights, answering questions such as:

- What are the best-selling products?
- Which countries generate the most sales and revenue?
- Who are the most valuable customers, overall and per country?
- Which months and days of the week are busiest?

## Approach

1. **Load the data** from `Online Retail.xlsx` into a pandas DataFrame.
2. **Assess data quality** — inspect shape, data types, summary statistics,
   duplicate rows, and missing values.
3. **Clean the data** via a reusable `clean_data()` function:
   - drop duplicate rows,
   - remove records with a missing `CustomerID`,
   - separate out cancellations (invoices flagged with a leading `C`) so
     returns don't distort sales totals,
   - engineer `Year`, `Month`, `DayofWeek`, and `Revenue` features.
4. **Test distributions & check outliers** — run Shapiro-Wilk normality tests
   on `Quantity` and `UnitPrice`, and inspect their distributions with
   log-scale boxplots to spot extreme values before aggregating.
5. **Analyze & aggregate** — group by product, customer, country, month, and
   day of week to rank performance by both quantity sold and revenue.
6. **Visualize** — plot the top 10 products, top countries, and the busiest
   months, and use a regression plot with a Pearson correlation to examine the
   relationship between month and units sold.

## Solution

The cleaned dataset feeds a set of grouped aggregations and charts that report:

- **Best-selling product** and **most valuable customer**.
- **Top 10 products** and **top 10 countries** by quantity sold.
- **Busiest month and day of the week** — measured by both units sold and
  revenue.
- **Top customer in each country** by quantity purchased.
- **Top-selling product in each country** by quantity sold.

All logic is organized into reusable functions so the same analysis can be
re-run on updated data with minimal changes.

## Concluding Remarks

This project demonstrates an end-to-end EDA workflow — from raw, imperfect data
to clean, interpretable business insights. The function-based structure makes
the pipeline easy to maintain and extend. Natural next steps would include
customer segmentation (e.g. RFM analysis), cohort/retention analysis, and time
-series forecasting of demand.

## Contents

- `analysis.ipynb` — the full EDA notebook.
- `Online Retail.xlsx` — the source dataset used in the analysis.

## Getting Started

```bash
# create and activate a virtual environment
python3 -m venv .venv
source .venv/bin/activate

# install dependencies
pip install pandas numpy matplotlib seaborn scipy openpyxl jupyter

# launch the notebook
jupyter notebook analysis.ipynb
```
