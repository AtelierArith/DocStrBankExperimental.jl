```
fit(
    gmm::GMM,
    data::AbstractMatrix{<:Real},
    k::Integer
)
```

The `fit` function performs the GMM clustering algorithm and returns a result object representing the clustering result.

# Parameters:

  * `gmm`: an instance representing the clustering settings and parameters.
  * `data`: a floating-point matrix, where each row represents a data point, and each column represents a feature.
  * `k`: an integer representing the number of clusters.

# Example

```julia
n = 100
d = 2
k = 2

data = rand(n, d)

gmm = GMM(estimator = EmpiricalCovarianceMatrix(n, d))
result = fit(gmm, data, k)
```
