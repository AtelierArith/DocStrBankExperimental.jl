```
kmeanspp_initialization(data::Vector{Float64}, k_means::Int)
```

Perform K-means++ initialization for cluster centroids on vector data.

# Arguments

  * `data::Vector{Float64}`: The input data vector.
  * `k_means::Int`: The number of clusters.

# Returns

  * A matrix of initial centroids for K-means clustering.
