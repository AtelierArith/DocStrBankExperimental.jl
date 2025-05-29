```
kmeans_clustering(data::Vector{Float64}, k_means::Int, max_iters::Int=100, tol::Float64=1e-6)
```

Perform K-means clustering on vector data.

# Arguments

  * `data::Vector{Float64}`: The input data vector.
  * `k_means::Int`: The number of clusters.
  * `max_iters::Int=100`: Maximum number of iterations.
  * `tol::Float64=1e-6`: Convergence tolerance.

# Returns

  * A tuple containing the final centroids and cluster labels for each data point.
