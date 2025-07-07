# MSCS_634_Lab_5_Wine_Clustering

**Student:** Romika Souda  
**Course:** MSCS 634  
**Lab:** Lab 5 – Clustering Techniques on the Wine Dataset  

## Overview  
In this lab, I applied Hierarchical (Agglomerative) and DBSCAN clustering algorithms to the Wine dataset from scikit-learn. My goal was to explore how these clustering techniques organize the data, compare their parameter sensitivities, and evaluate their performance using visualizations and clustering metrics.

## What I Did  
1. **Data Preparation & Exploration**  
   - I loaded the Wine dataset and converted it to a pandas DataFrame.  
   - I examined the first few rows, data types, and summary statistics.  
   - I standardized all features to mean = 0 and variance = 1 to ensure fair clustering.  

2. **Hierarchical Clustering**  
   - I ran AgglomerativeClustering for different values of `n_clusters` (2, 3, and 4).  
   - I plotted the first two standardized features colored by cluster label.  
   - I generated a truncated dendrogram (p = 5) to visualize how samples merge at each linkage distance.  

3. **DBSCAN Clustering**  
   - I experimented with multiple settings of `eps` (0.3, 0.5, 1.0) and `min_samples` (3, 5).  
   - I visualized cluster assignments—including noise points (label = –1).  
   - I computed **Silhouette Score** (excluding noise), **Homogeneity Score**, and **Completeness Score** for each parameter combination.  

4. **Analysis & Insights**  
   - I compared how hierarchical and density-based methods group the same data.  
   - I observed that Hierarchical Clustering produces cleaner, fixed-size clusters but requires choosing the number of clusters up front.  
   - I noted that DBSCAN automatically identifies noise/outliers, but its results depend heavily on choosing the right `eps` and `min_samples`.  
   - I reflected on strengths/weaknesses:  
     - *Hierarchical*: easy to interpret via dendrograms, but inflexible in cluster count.  
     - *DBSCAN*: robust to outliers and finds arbitrarily shaped clusters, but parameter tuning can be tricky.

## Key Insights  
- A cluster count of **3** in Hierarchical Clustering most closely matched the three true wine classes when visualized on the first two principal features.  
- DBSCAN with **eps = 0.5** and **min_samples = 5** balanced the trade-off between identifying dense regions and not calling too many points “noise.”  
- Silhouette Scores varied across methods; Hierarchical generally showed higher scores on the selected feature pair, while DBSCAN provided valuable noise detection.

## Challenges & Decisions  
- **Choosing `eps` for DBSCAN**: I plotted distance-to-nearest-neighbors graphs to estimate a “knee” point, but I still had to experiment.  
- **Interpreting the dendrogram**: Truncating at p = 5 helped keep the plot readable, but I had to decide which linkage distances were meaningful.  
- **Metric limitations**: Silhouette only applies to clusters (not noise), and Homogeneity/Completeness compare to ground truth labels—which we often don’t have in real-world clustering tasks.

---

Feel free to clone this repository and run the notebook (`MSCS_634_Lab_5.ipynb`) to reproduce my results or explore further parameter settings.  
