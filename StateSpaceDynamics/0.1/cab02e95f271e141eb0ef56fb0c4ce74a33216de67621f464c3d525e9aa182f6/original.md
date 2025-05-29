```
kmeanspp_initialization(data::Matrix{<:Real}, k_means::Int)
```

Perform K-means++ initialization for cluster centroids.

# Arguments

  * `data::Matrix{<:Real}`: The input data matrix where each row is a data point.
  * `k_means::Int`: The number of clusters.

# Returns

  * A matrix of initial centroids for K-means clustering.
