```
kmeans_clustering(data::Matrix{<:Real}, k_means::Int, max_iters::Int=100, tol::Float64=1e-6)
```

Perform K-means clustering on the input data.

# Arguments

  * `data::Matrix{<:Real}`: The input data matrix where each row is a data point.
  * `k_means::Int`: The number of clusters.
  * `max_iters::Int=100`: Maximum number of iterations.
  * `tol::Float64=1e-6`: Convergence tolerance.

# Returns

  * A tuple containing the final centroids and cluster labels for each data point.
