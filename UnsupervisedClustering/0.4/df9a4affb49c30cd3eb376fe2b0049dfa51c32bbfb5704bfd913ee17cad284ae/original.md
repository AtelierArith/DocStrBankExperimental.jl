```
fit(
    kmedoids::Kmedoids,
    distances::AbstractMatrix{<:Real},
    initial_clusters::AbstractVector{<:Integer}
)
```

The `fit` function performs the k-medoids clustering algorithm on the given data points as the initial point and returns a result object representing the clustering result.

# Parameters:

  * `kmedoids`: an instance representing the clustering settings and parameters.
  * `distances`: a floating-point matrix representing the pairwise distances between the data points.
  * `initial_clusters`: an integer vector where each element is the initial data point for each cluster.

# Example

```julia
n = 100
d = 2
k = 2

data = rand(n, d)
distances = pairwise(SqEuclidean(), data, dims = 1)

kmedoids = Kmedoids()
result = fit(kmedoids, distances, [4, 12])
```
