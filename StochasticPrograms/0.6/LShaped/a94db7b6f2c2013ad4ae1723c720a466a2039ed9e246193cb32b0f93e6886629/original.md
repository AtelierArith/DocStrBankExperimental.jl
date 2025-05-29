```
Hierarchical(nclusters::Int; distance::Function = absolute_distance, linkage::Symbol = :single)
```

Buffered cuts are sorted into `nclusters` clusters, using a Hierarchical algorithm, with the given `linkage`, over a generalized `distance` matrix.

The following distance measures are available

  * [`absolute_distance`](@ref)
  * [`angular_distance`](@ref)
  * [`spatioangular_distance`](@ref
