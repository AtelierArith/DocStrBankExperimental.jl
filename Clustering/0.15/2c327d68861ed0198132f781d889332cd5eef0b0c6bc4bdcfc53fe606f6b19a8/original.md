```
DbscanResult <: ClusteringResult
```

The output of [`dbscan`](@ref) function.

## Fields

  * `clusters::Vector{DbscanCluster}`: clusters, length *K*
  * `seeds::Vector{Int}`: indices of the first points of each cluster's *core*, length *K*
  * `counts::Vector{Int}`: cluster sizes (number of assigned points), length *K*
  * `assignments::Vector{Int}`: vector of clusters indices, where each point was assigned to, length *N*
