# Slooze_data_challenge

# Inventory & Supply Chain Optimization Project (2016 Data)

## Project Overview

This project provides a comprehensive analysis of sales and purchase data from 2016 to optimize inventory management and enhance supply chain efficiency. It covers demand forecasting, inventory classification (ABC Analysis), supplier performance evaluation (including lead time analysis), and the calculation of optimal ordering quantities (EOQ) and reorder points (ROP).

The goal is to move towards a data-driven inventory strategy, minimizing costs associated with holding inventory and preventing stockouts, ultimately leading to improved financial performance and operational excellence.

## Table of Contents

1.  [Project Objectives](#project-objectives)
2.  [Tasks Performed](#tasks-performed)
3.  [How to Run the Code](#how-to-run-the-code)
4.  [Key Findings & Insights](#key-findings--insights)
5.  [Potential Future Enhancements](#potential-future-enhancements)

## Project Objectives

* **Inventory Optimization:** Determine ideal inventory levels for different product categories.
* **Sales & Purchase Insights:** Identify sales trends, top-performing products, and supplier efficiency.
* **Process Improvement:** Optimize procurement and stock control to minimize financial loss.

## Tasks Performed

This project addresses a series of interconnected tasks:

1.  ### Demand Forecasting
    * **Purpose:** To predict future demand for products based on historical sales data.
    * **Methodology:** Used time-series analysis, specifically the **SARIMA model**, on the top-selling `Brand 8111`'s daily sales data.
    * **Output:** Sales forecasts to guide future inventory planning.

2.  ### ABC Analysis
    * **Purpose:** To classify inventory items (brands) based on their sales value contribution.
    * **Methodology:** Applied the Pareto Principle to categorize brands into A (high value), B (moderate value), and C (low value) groups.
    * **Output:** A prioritized list of brands, enabling differentiated management strategies where 'A' items receive the most rigorous attention.

3.  ### Supplier Performance & Lead Time Analysis
    * **Purpose:** To assess the efficiency and reliability of suppliers and optimize procurement timelines.
    * **Methodology:** Analyzed purchase data to identify:
        * Total spend and quantity purchased from each vendor.
        * Average payment adherence (days to pay invoices).
        * **Crucially, Delivery Lead Time Performance:** Calculated the average lead time (days from `PODate` - Order Placement Date - to `ReceivingDate` - Actual Receipt Date) and its **Standard Deviation**. The standard deviation is a key metric for assessing the *consistency* and *predictability* of deliveries.
    * **Output:** Detailed vendor performance metrics and a scatter plot visualizing average lead time vs. lead time standard deviation, highlighting reliable vs. unreliable suppliers.

4.  ### Inventory Optimization (Economic Order Quantity (EOQ) & Reorder Point (ROP))
    * **Purpose:** To determine the optimal quantity to order and the ideal inventory level at which to place a new order.
    * **Methodology:** Applied the classic EOQ formula (minimizing ordering and holding costs) and ROP formula (factoring in average daily demand, supplier lead time, and a conceptual safety stock for variability) for `Brand 8111`. Assumed values were used for ordering and holding costs.
    * **Output:** Recommended EOQ (how much to order) and ROP (when to order) for the analyzed product.

## How to Run the Code

To execute the analysis and replicate the results, follow these steps:

1.  **Prerequisites:**
    * Python 3.x installed.
    * Jupyter Notebook or JupyterLab (recommended) or any Python IDE.
    * Required Python libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `statsmodels`. You can install them using pip:
        ```bash
        pip install pandas numpy matplotlib seaborn statsmodels
        ```

2.  **Data Files:**
    * Ensure the following CSV files are present in the **same directory** as your Python script or Jupyter Notebook:
        * 2017PurchasePricesDec.csv
        * BegInvFINAL12312016.csv
        * EndInvFINAL12312016.csv
        * InvoicePurchases12312016.csv
        * PurchasesFINAL12312016.csv
        * SalesFINAL12312016.csv
    * *If your data files are in a different location, you will need to update the `pd.read_csv()` paths in the code accordingly.*

3.  **Execution:**
    * Open the Jupyter Notebook (`.ipynb` file) or Python script (`.py` file) in your chosen environment.
    * Run the cells sequentially. The code is structured to perform each task in order, building upon previous results.

## Key Findings & Insights

* **Dominant Brands:** A small percentage of brands (`A-items`) account for the vast majority of sales value, requiring focused inventory management.
* **Consistent Payment Cycle:** The company maintains a fairly consistent payment cycle of around 35-37 days for most vendors.
* **Lead Time Variability is Key:** While average lead times are consistent across top suppliers (7-8 days), the *standard deviation* of lead time highlights variations in reliability, which directly impacts safety stock requirements. More consistent suppliers allow for leaner inventories.
* **Actionable Inventory Parameters:** EOQ and Reorder Point calculations provide concrete figures for optimizing order sizes and timing, minimizing costs and preventing stockouts for critical items.
* **Data-Driven Procurement:** Supplier performance metrics enable informed decisions for vendor selection, relationship management, and negotiation.

## Potential Future Enhancements

* **Dynamic Cost Inputs:** Incorporate actual ordering and holding cost data from financial systems instead of assumptions.
* **Service Level Optimization:** Perform more sophisticated safety stock calculations based on desired service levels and historical demand/lead time variability.
* **Quantity Discounts:** Integrate logic for quantity discounts into EOQ calculations.
* **Minimum Order Quantities (MOQs):** Account for supplier-imposed MOQs when determining order sizes.
* **Multi-Item Optimization:** Extend EOQ/ROP to optimize across multiple products and considering shared resources.
* **Automated Reporting:** Develop dashboards to visualize key inventory and supplier performance metrics in real-time.
* **Price Competitiveness Analysis:** Compare purchase prices for similar items across different vendors to assess pricing competitiveness.
