```
fit(chain::ClusteringChain, data::AbstractMatrix{<:Real}, k::Integer)
```

The `fit` function applies a sequence of clustering algorithms and returns a result object representing the clustering outcome.

# Parameters:

  * `meta`: an instance representing the clustering settings and parameters.
  * `data`: a floating-point matrix, where each row represents a data point, and each column represents a feature.
  * `k`: an integer representing the number of clusters.

# Example

```julia
n = 100
d = 2
k = 2

data = rand(n, d)

kmeans = Kmeans()
gmm = GMM(estimator = EmpiricalCovarianceMatrix(n, d))

chain = ClusteringChain(kmeans, gmm)
result = fit(chain, data, k)
```
