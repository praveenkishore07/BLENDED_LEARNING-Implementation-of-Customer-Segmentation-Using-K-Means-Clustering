# BLENDED LEARNING
# Implementation of Customer Segmentation Using K-Means Clustering

## AIM:
To implement customer segmentation using K-Means clustering on the Mall Customers dataset to group customers based on purchasing habits.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm :

1. Import required libraries such as pandas, matplotlib, seaborn, sklearn KMeans, StandardScaler, and silhouette_score.

2. Load the dataset CustomerData.csv and select features Age, Annual Income, and Spending Score.

3. Normalize the selected features using StandardScaler to standardize the data.

4. Apply the Elbow Method using K-Means to determine the optimal number of clusters.

5. Train the K-Means model with the optimal clusters, assign cluster labels, evaluate using silhouette score, and visualize customer segments using a scatter plot. 

## Program:
```
/*
Program to implement customer segmentation using K-Means clustering on the Mall Customers dataset.
Developed by: A PRAVEEN KISHORE
RegisterNumber: 212225220074

Program to implement customer segmentation using K-Means clustering on the Mall Customers dataset.

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler
from sklearn.metrics import silhouette_score


data = pd.read_csv("CustomerData.csv")


print(data.head())
print(data.columns)


features = ['Age', 'Annual Income (k$)', 'Spending Score (1-100)']
X = data[features]


scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)


wcss = [] 
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, random_state=42)
    kmeans.fit(X_scaled)
    wcss.append(kmeans.inertia_)


plt.figure(figsize=(8, 4))
plt.plot(range(1, 11), wcss, marker='o', linestyle='--')
plt.xlabel('Number of Clusters')
plt.ylabel('WCSS')
plt.title('Elbow Method for Optimal Number of Clusters')
plt.show()


optimal_clusters = 4
kmeans = KMeans(n_clusters=optimal_clusters, random_state=42)
kmeans.fit(X_scaled)


data['Cluster'] = kmeans.labels_


sil_score = silhouette_score(X_scaled, kmeans.labels_)
print(f"Silhouette Score: {sil_score}")

plt.figure(figsize=(10, 6))
sns.scatterplot(data=data, x='Annual Income (k$)', y='Spending Score (1-100)', hue='Cluster', palette='viridis', s=100, alpha=0.7)
plt.title('Customer Segmentation based on Annual Income and Spending Score')
plt.xlabel('Annual Income (k$)')
plt.ylabel('Spending Score (1-100)')
plt.legend(title='Cluster')
plt.show()

*/
```

## Output:
<img width="1779" height="873" alt="image" src="https://github.com/user-attachments/assets/e35227d2-e181-428a-9fda-a93e601f7160" />
<img width="1037" height="132" alt="image" src="https://github.com/user-attachments/assets/34bf3d1e-b2eb-4438-8f75-f7c09d8f9159" />
<img width="1759" height="812" alt="image" src="https://github.com/user-attachments/assets/ac708d83-9d4a-4dc3-914c-8da68d09666e" />




## Result:
Thus, customer segmentation was successfully implemented using K-Means clustering, grouping customers into distinct segments based on their annual income and spending score. 
