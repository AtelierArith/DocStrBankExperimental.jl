```
fit(
    kmeans::Kmeans,
    data::AbstractMatrix{<:Real},
    initial_clusters::AbstractVector{<:Integer}
)
```

The `fit` function performs the k-means clustering algorithm on the given data points as the initial point and returns a result object representing the clustering result.

# Parameters:

  * `kmeans`: an instance representing the clustering settings and parameters.
  * `data`: a floating-point matrix, where each row represents a data point, and each column represents a feature.
  * `initial_clusters`: an integer vector where each element is the initial data point for each cluster.

# Example

```julia
n = 100
d = 2
k = 2

data = rand(n, d)

kmeans = Kmeans()
result = fit(kmeans, data, [4, 12])
```
