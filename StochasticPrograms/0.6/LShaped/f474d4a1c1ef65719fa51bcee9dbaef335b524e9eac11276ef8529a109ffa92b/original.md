```
ClusterByReference(τ::AbstractFloat; distance::Function = absolute_distance)
```

Buffered cuts are aggregated if within the tolerance `τ` to a reference cut, according the supplied `distance` function. Behaves as multi-cut otherwise.

The following distance measures are available

  * [`absolute_distance`](@ref)
  * [`angular_distance`](@ref)
  * [`spatioangular_distance`](@ref
