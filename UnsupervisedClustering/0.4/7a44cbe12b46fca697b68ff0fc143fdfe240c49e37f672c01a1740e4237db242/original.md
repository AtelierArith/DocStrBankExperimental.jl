```
fit!(
    kmedoids::Kmedoids,
    distances::AbstractMatrix{<:Real},
    result::KmedoidsResult
)
```

The `fit!` function performs the k-medoids clustering algorithm on the given result as the initial point and updates the provided object with the clustering result.

# Parameters:

  * `kmedoids`: an instance representing the clustering settings and parameters.
  * `distances`: a floating-point matrix representing the pairwise distances between the data points.
  * `result`: a result object that will be updated with the clustering result.

# Example

```julia
n = 100
d = 2
k = 2

data = rand(n, d)
distances = pairwise(SqEuclidean(), data, dims = 1)

kmedoids = Kmedoids()
result = KmedoidsResult(n, [1.0 2.0; 1.0 2.0])
fit!(kmedoids, distances, result)
```
