```
Kmedoids(nclusters::Int; distance::Function = absolute_distance)
```

Buffered cuts are sorted into `nclusters` clusters, using a K-medoids algorithm over a generalized `distance` matrix.

The following distance measures are available

  * [`absolute_distance`](@ref)
  * [`angular_distance`](@ref)
  * [`spatioangular_distance`](@ref
