# 🛍️ Customer Segmentation: PCA, Clustering & Behavioral Profiling

> **From customer data to meaningful segments — using feature engineering, dimensionality reduction, and clustering to uncover actionable customer profiles.**

---

## 📌 Project Overview

Customer segmentation is the process of identifying groups of customers who share similar characteristics, behaviors, or purchasing patterns.

This project applies **Unsupervised Machine Learning** to a customer marketing dataset containing **2,240 customers across 29 attributes** to:

1. Perform structured exploratory data analysis (EDA)
2. Clean and prepare customer-level data
3. Engineer behavioral and household-level features
4. Standardize the analytical feature space
5. Apply **Principal Component Analysis (PCA)**
6. Explore customer segments using **K-Means and Agglomerative Clustering**
7. Profile the resulting customer groups
8. Translate cluster characteristics into actionable marketing recommendations

The project focuses on moving beyond simply creating clusters to answering:

> **Who are these customers, how are they different, and what could a business do differently because of those differences?**

---

## 🎯 Business Problem

> **Can customer demographic, household, spending, and purchasing behavior be used to identify meaningful customer segments and support differentiated marketing strategies?**

A single marketing strategy may not be equally effective across all customers.

A high-income customer with strong purchasing activity may respond differently to a value-focused family household, while a younger household with children may have different product and engagement needs.

This project uses unsupervised learning to uncover these customer patterns.

---

## 🗂️ Dataset

The project uses a customer marketing campaign dataset containing demographic, household, spending, purchasing, and campaign-related attributes.

| Attribute | Detail |
|---|---:|
| Records | 2,240 customers |
| Original Features | 29 |
| Final Analytical Customers | ~2,212 |
| Learning Type | Unsupervised Learning |
| Primary Task | Customer Segmentation |

### Feature Groups

| Category | Examples |
|---|---|
| Demographics | Year of Birth, Education, Marital Status |
| Household | Kidhome, Teenhome |
| Spending | Wine, Fruits, Meat, Fish, Sweets, Gold |
| Purchasing | Web, Catalog, Store Purchases |
| Engagement | Recency, Web Visits |
| Campaigns | Campaign Acceptance, Response |
| Customer History | Enrollment Date / Tenure |

> **Note:** Campaign-response variables are used for downstream profiling rather than defining the customer segments themselves.

---

## 🔧 Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3 |
| Data Wrangling | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Machine Learning | scikit-learn |
| Dimensionality Reduction | PCA |
| Clustering | K-Means, Agglomerative Clustering |
| Environment | Jupyter Notebook |

---

## 🧹 Data Preparation & Cleaning

The dataset was audited to understand its structure and data quality.

The preparation process included:

- Dataset structure inspection
- Data-type validation
- Missing-value assessment
- Duplicate checks
- Identification of unrealistic demographic values
- Filtering of extreme age/income records
- Numerical and categorical feature validation
- Preparation of the final analytical dataset

After cleaning and filtering, approximately **2,212 customer records** were retained.

---

## 🛠️ Feature Engineering

Several customer-level features were engineered to provide a more meaningful representation of customer behavior.

| Feature | Definition | Purpose |
|---|---|---|
| `Age` | Current Year − Year of Birth | Customer demographic profile |
| `Spent` | Sum of major product-category spending | Overall purchasing value |
| `Children` | Kidhome + Teenhome | Household structure |
| `Family_Size` | Household + children | Household size |
| `Is_Parent` | Whether customer has children | Parent/non-parent segmentation |
| `Customer_For` | Derived from enrollment information | Customer tenure |

### Total Spending

```text
Spent = Wine + Fruits + Meat + Fish + Sweets + Gold
```

### Number of Children

```text
Children = Kidhome + Teenhome
```

These engineered features provide a more meaningful representation of customer demographics, household structure, and purchasing behavior.

---

## 📊 Exploratory Data Analysis

The EDA stage focused on understanding customer behavior before applying clustering algorithms.

The analysis included:

- Numerical feature distributions
- Customer age and income patterns
- Spending distributions
- Household characteristics
- Purchasing behavior
- Product-category spending
- Campaign engagement
- Relationships between customer characteristics
- Outlier inspection
- Comparative customer profiling

EDA was used to guide preprocessing and feature-engineering decisions.

---

## ⚙️ Feature Preprocessing

Because clustering algorithms rely heavily on distances between observations, preprocessing is an important part of the modeling workflow.

```text
Numerical Features
        ↓
Missing Value Treatment
        ↓
Standardization
        ↓
Scaled Numerical Features

Categorical Features
        ↓
Encoding
        ↓
Numerical Representation

        ↓
Combined Feature Matrix
```

### Feature Scaling

Standardization was applied because variables exist on different numerical scales.

Without scaling, high-magnitude variables could disproportionately influence distance calculations.

---

# 📉 Principal Component Analysis (PCA)

**Principal Component Analysis (PCA)** was applied for dimensionality reduction.

Three principal components were used for the lower-dimensional representation.

The first three components explain approximately:

> **55% of the total standardized variance**

PCA was used to:

- Reduce dimensionality
- Create a compact feature representation
- Identify major directions of variation
- Support cluster visualization
- Simplify interpretation of the feature space

The three components do **not** capture all information in the original feature space; they retain approximately 55% of standardized variance.

---

## 🤖 Clustering Approach

Two unsupervised learning approaches were explored.

### 1. K-Means Clustering

K-Means groups observations around cluster centroids by minimizing within-cluster variation.

An elbow-based analysis was used to investigate the relationship between cluster count and within-cluster variation.

### 2. Agglomerative Hierarchical Clustering

Agglomerative clustering builds a hierarchy of customer groups by progressively merging similar observations or clusters.

The resulting clusters were profiled using original business variables.

---

## 📈 Cluster Profiling

After clustering, the resulting groups were analyzed using:

- Income
- Total spending
- Age
- Family size
- Parenthood
- Number of children
- Purchasing behavior
- Promotional engagement
- Household characteristics

This transforms abstract cluster labels into interpretable customer profiles.

---

# 👥 Customer Segment Findings

## Cluster 0 — Higher-Spending Family Customers

### Profile

- Parent households
- Family sizes between 2 and 4 members
- Some households include teenagers
- Relatively older customers
- Higher spending behavior
- Comparatively stronger income profile

### Potential Marketing Direction

**Goal:** Focus on convenience and family value.

Potential actions:

- Family-sized product bundles
- Multi-buy offers
- Household value packs
- Convenience-oriented products
- Ready-made meal solutions
- Family-focused promotions

---

## Cluster 1 — Younger, Smaller Families

### Profile

- Majority are parents
- Smaller households
- Typically one child
- Relatively younger customers
- Limited presence of teenagers

### Potential Marketing Direction

**Goal:** Focus on child-oriented products, quality, and convenience.

Potential actions:

- Child-focused product promotions
- Fresh and health-oriented products
- Personalized digital coupons
- Family-focused offers
- Mobile/app-based promotions
- Convenience-oriented shopping experiences

---

## Cluster 2 — High-Income, High-Spending Non-Parents

### Profile

- Predominantly non-parent households
- Small household sizes
- High-income profile
- High overall spending
- Customers span multiple age groups
- Slight majority of couples over single customers

### Potential Marketing Direction

**Goal:** Focus on premium, specialty, and higher-margin products.

Potential actions:

- Premium product categories
- Specialty and international products
- Premium bundles
- Exclusive product launches
- Personalized premium offers
- Experience-oriented promotions

---

## Cluster 3 — Larger, Lower-Income Families

### Profile

- Parent households
- Family sizes between 2 and 5 members
- Majority have teenagers
- Relatively older customers
- Lower-income profile
- Lower spending compared with the highest-value segment

### Potential Marketing Direction

**Goal:** Focus on value, savings, and larger-volume purchases.

Potential actions:

- Private-label products
- Bulk purchasing options
- Family-sized products
- Weekly value promotions
- Loyalty rewards
- Savings-focused offers

---

# 💡 Key Business Findings

### 1. Income and spending vary across segments

The segmentation identifies differences between higher-income/high-spending customers and lower-income/value-oriented households.

### 2. Household structure is an important differentiator

Parenthood, number of children, family size, and presence of teenagers contribute to differences between customer groups.

### 3. High-income non-parent customers form a distinctive segment

One segment is strongly characterized by high income, high spending, and very low parent representation.

### 4. Parent customers are not homogeneous

The analysis identifies multiple family-oriented groups with different income levels, household sizes, ages, and spending behavior.

### 5. Segmentation enables differentiated marketing

The customer base can be approached through different strategies for premium, family-oriented, younger-household, and value-sensitive segments.

---

# 🎯 Business Recommendations

| Segment | Primary Focus | Potential Strategy |
|---|---|---|
| Higher-Spending Families | Convenience & family value | Bundles, multi-buy offers |
| Younger Families | Child & health-focused products | Digital offers, personalized coupons |
| High-Income Non-Parents | Premium experiences | Specialty products, premium bundles |
| Lower-Income Families | Value & savings | Private label, bulk offers, loyalty rewards |

These recommendations are **business hypotheses derived from observed cluster characteristics** and should be validated through controlled experiments or campaign-response analysis.

---

# 🧠 Machine Learning Concepts Demonstrated

### Unsupervised Learning
- Customer segmentation
- Pattern discovery
- Cluster analysis

### Dimensionality Reduction
- Principal Component Analysis
- Explained variance analysis
- Lower-dimensional representations

### Clustering
- K-Means Clustering
- Agglomerative Hierarchical Clustering

### Data Preparation
- Missing-value handling
- Feature engineering
- Categorical encoding
- Feature scaling

### Analytical Techniques
- Exploratory Data Analysis
- Customer profiling
- Cluster comparison
- Distribution analysis
- Behavioral analysis

### Business Application
- Customer profiling
- Segment interpretation
- Marketing strategy development
- Data-driven decision support

---

# 📏 Cluster Validation & Model Evaluation

Unlike supervised classification, clustering does not have predefined ground-truth labels.

Therefore, traditional accuracy is not appropriate for evaluating the segmentation.

A stronger evaluation framework should include:

### Silhouette Score
Measures how similar an observation is to its own cluster compared with other clusters. Higher values generally indicate better separation.

### Davies-Bouldin Index
Measures similarity between clusters based on within-cluster dispersion and between-cluster separation. Lower values are generally preferred.

### Calinski-Harabasz Index
Measures the ratio of between-cluster dispersion to within-cluster dispersion. Higher values generally indicate stronger cluster structure.

These metrics can be used to compare:

- Different cluster counts
- K-Means vs. hierarchical clustering
- Different feature representations
- PCA vs. non-PCA representations

---

# 🔬 Methodological Considerations

### Why Feature Engineering?

Raw variables may not directly represent the business concepts required for segmentation.

For example:

```text
Wine + Fruits + Meat + Fish + Sweets + Gold
                    ↓
              Total Spending
```

Similarly:

```text
Kidhome + Teenhome
        ↓
    Children
```

These transformations create features that better represent customer behavior.

### Why Scaling?

Distance-based algorithms are sensitive to feature magnitude. Scaling prevents high-magnitude variables from dominating the clustering process.

### Why PCA?

PCA provides a lower-dimensional representation of correlated features and supports visualization and dimensionality reduction.

### Why Clustering?

There is no predefined customer-segment label in the dataset. Clustering allows customer groups to be discovered from the available features.

### Why Profile Using Original Features?

PCA components are mathematically useful but difficult to interpret from a business perspective. Therefore, clusters are profiled using original variables such as income, spending, family size, age, and purchasing behavior.

---

# ⚠️ Limitations

1. **PCA retains approximately 55% variance using three components.** The representation is useful for dimensionality reduction but does not capture all variation.
2. **Cluster selection requires systematic validation.** Different cluster counts and algorithms should be compared using multiple internal metrics.
3. **Encoding strategy can affect clustering.** Alternative categorical representations should be evaluated.
4. **Clustering does not establish causality.** The segments describe patterns rather than causal relationships.
5. **Marketing recommendations require experimentation.** The proposed strategies are hypotheses and should be validated through controlled campaigns.

---

# 🚀 Future Improvements

## Model Validation

- Add Silhouette Score
- Add Davies-Bouldin Index
- Add Calinski-Harabasz Index
- Compare multiple cluster counts
- Compare K-Means and hierarchical clustering systematically

## Feature Representation

- Evaluate alternative categorical encoding methods
- Compare clustering with and without PCA
- Test PCA configurations retaining higher explained variance
- Evaluate different feature combinations

## Additional Algorithms

Potential future experiments:

- DBSCAN
- Gaussian Mixture Models
- Alternative hierarchical clustering methods

## Business Validation

```text
Customer Segment
       ↓
Targeted Campaign
       ↓
Control vs Treatment
       ↓
Measure Response
       ↓
Evaluate Incremental Impact
       ↓
Refine Segmentation
```

This would move the project from descriptive segmentation toward experiment-driven customer analytics.

---

# 📁 Repository Structure

```text
Customer-Segmentation/
│
├── Customer_Segmentation_proj.ipynb
├── marketing_campaign.csv
├── Customer_segmentation_proj.docx
└── README.md
```

---

# ▶️ How to Run

### 1. Clone the repository

```bash
git clone <repository-url>
cd Customer-Segmentation
```

### 2. Install dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 4. Open the notebook

```text
Customer_Segmentation_proj.ipynb
```

Run the notebook sequentially to reproduce the analysis.

---

# 📌 Project Takeaway

> **A cluster has little business value until we understand who belongs to it and what decision the business can make differently because of it.**

The project connects:

```text
Customer Data
      ↓
Feature Engineering
      ↓
Data Preprocessing
      ↓
PCA
      ↓
Clustering
      ↓
Customer Profiling
      ↓
Business Insights
      ↓
Marketing Strategy
```

The central goal is to demonstrate how **unsupervised machine learning can move beyond algorithmic clustering and support practical, customer-focused decision-making.**

---

# 👤 Author

**Sindhu M**

**M.Sc. Business Statistics**  
Vellore Institute of Technology

**Data Science | Machine Learning | Business Analytics | Power BI**

### Areas of Interest

`Data Science` · `Machine Learning` · `Customer Analytics` · `Business Analytics` · `Data Visualization`

### Links

- 🌐 Portfolio: https://sindhuportfolio-ab4p.vercel.app
- 💻 GitHub: https://github.com/sindhumanoharan1210
- 🔗 LinkedIn: https://linkedin.com/in/sindhumanoharan/

---

## ⚠️ Disclaimer

This project is intended for educational and portfolio purposes.

The customer segments and marketing recommendations are based on patterns observed in the available dataset. They represent **analytical insights and testable business hypotheses**, not causal conclusions or guaranteed marketing outcomes.
