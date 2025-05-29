```
DbscanCluster
```

DBSCAN cluster, part of [`DbscanResult`](@ref) returned by [`dbscan`](@ref) function.

## Fields

  * `size::Int`: number of points in a cluster (core + boundary)
  * `core_indices::Vector{Int}`: indices of points in the cluster *core*, a.k.a. *seeds*  (have at least `min_neighbors` neighbors in the cluster)
  * `boundary_indices::Vector{Int}`: indices of the cluster points outside of *core*
