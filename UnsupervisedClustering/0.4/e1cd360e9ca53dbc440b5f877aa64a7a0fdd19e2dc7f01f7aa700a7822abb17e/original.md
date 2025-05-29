```
fit(
    kmeans::Kmeans,
    data::AbstractMatrix{<:Real},
    k::Integer
)
```

The `fit` function performs the k-means clustering algorithm and returns a result object representing the clustering result.

# Parameters:

  * `kmeans`: an instance representing the clustering settings and parameters.
  * `data`: a floating-point matrix, where each row represents a data point, and each column represents a feature.
  * `k`: an integer representing the number of clusters.

# Example

```julia
n = 100
d = 2
k = 2

data = rand(n, d)

kmeans = Kmeans()
result = fit(kmeans, data, k)
```
