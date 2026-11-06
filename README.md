# Healthcare Commercial Analytics: Territory Efficiency & OPEX Optimization

**Author:** Arpit Kumar  
**Tech Stack:** Python (Pandas, NumPy), MySQL, Power BI  
**Core Frameworks:** MECE Segmentation, Resource Allocation, ROI Optimization  

## 📌 Executive Summary
This project identifies, quantifies, and solves a commercial resource misallocation problem within a medical sales territory. By merging real-world CMS Medicare prescription data with simulated CRM interaction logs, an end-to-end data pipeline was engineered to mathematically prove that sales representatives were spending the majority of their Operating Expense (OPEX) hours on low-yielding accounts.

## ⚠️ The Business Problem
Medical sales representatives are misallocating their time and company resources. They are over-engaging doctors who write very few prescriptions while under-engaging the top-performing doctors who actually drive market revenue. This results in wasted operational spend and lost market share.

## 🛠️ Methodology & Technical Execution
This project relies strictly on first-principles data engineering and statistical grouping, avoiding "black box" machine learning models to ensure all logic remains highly defensible and actionable.

1. **Data Extraction & Simulation (Python):** 
   * Extracted a targeted territory of 2,744 providers from a 4GB+ CMS Medicare Part D dataset using chunking in Pandas.
   * Programmed a synthetic CRM interaction dataset to mathematically mirror the operational inefficiency (inverse relationship between prescription volume and sales visits).
2. **Data Transformation & MECE Segmentation (MySQL):** 
   * Built an ETL pipeline utilizing Common Table Expressions (CTEs) and `LEFT JOINs` to aggregate provider-level activity.
   * Applied the `NTILE(3)` window function to establish a Mutually Exclusive, Collectively Exhaustive (MECE) framework, dynamically segmenting the market into Tier 1 (High Value), Tier 2 (Medium Value), and Tier 3 (Low Value) based purely on true commercial yield.
3. **Business Intelligence (Power BI):** 
   * Developed a one-page executive dashboard designed for a Regional Sales Director.
   * Visualized the "engagement-to-yield" mismatch and calculated exact Wasted OPEX Hours directly from the SQL view, completely eliminating the need for complex DAX formulas.

## 📊 Key Findings
The data mathematically proved a severe breakdown in territory efficiency:
* **High Yield, Low Focus:** Tier 1 providers drove **78.6%** of the total prescription volume but were severely under-engaged by the sales force.
* **Low Yield, High Focus:** Tier 3 providers consumed **55.0%** of all sales calls despite contributing minimal revenue.
* **Financial Leak:** The sales force spent **14,005 Wasted OPEX Hours** sitting in unproductive meetings with bottom-tier targets.

## 💡 Strategic Recommendation
**Reallocate 20% to 25% of total daily call volume away from Tier 3 accounts and redirect it strictly to Tier 1 accounts.** 

*Defensibility Note:* While the total leak is 55.0%, attempting to shift half of a sales team's routing schedule overnight would cause operational disruption. An incremental 20-25% shift acts as a realistic "Phase 1" commercial strategy, immediately capturing lost revenue from high-value doctors while allowing representatives time to establish new routing habits.
