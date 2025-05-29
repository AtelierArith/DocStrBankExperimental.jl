```
fit!(
    gmm::GMM,
    data::AbstractMatrix{<:Real},
    result::GMMResult
)
```

The `fit!` function performs the GMM clustering algorithm on the given result as the initial point and updates the provided object with the clustering result.

# Parameters:

  * `gmm`: an instance representing the clustering settings and parameters.
  * `data`: a floating-point matrix, where each row represents a data point, and each column represents a feature.
  * `result`: a result object that will be updated with the clustering result.

# Example

```julia
n = 100
d = 2
k = 2

data = rand(n, d)

gmm = GMM(estimator = EmpiricalCovarianceMatrix(n, d))
result = GMMResult(n, [[1.0, 1.0], [2.0, 2.0]])
fit!(gmm, data, result)
```
