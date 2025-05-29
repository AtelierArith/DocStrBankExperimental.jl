```
fit(
    kmedoids::Kmedoids,
    distances::AbstractMatrix{<:Real},
    k::Integer
)
```

The `fit` function performs the k-medoids clustering algorithm and returns a result object representing the clustering result.

# Parameters:

  * `kmedoids`: an instance representing the clustering settings and parameters.
  * `distances`: a floating-point matrix representing the pairwise distances between the data points.
  * `k`: an integer representing the number of clusters.

# Example

```julia
n = 100
d = 2
k = 2

data = rand(n, d)
distances = pairwise(SqEuclidean(), data, dims = 1)

kmedoids = Kmedoids()
result = fit(kmedoids, distances, k)
```
