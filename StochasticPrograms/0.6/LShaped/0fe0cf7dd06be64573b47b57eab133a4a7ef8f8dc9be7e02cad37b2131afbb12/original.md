```
SortByReference(τ::AbstractFloat; distance::Function = absolute_distance)
```

Incoming cuts are placed into an aggregate based on the distance to a reference cut, according the supplied `distance` function. Behaves as [`SelectClosest`](@ref) if not withing the tolerance `τ` to the reference cut.

The following distance measures are available

  * [`absolute_distance`](@ref)
  * [`angular_distance`](@ref)
  * [`spatioangular_distance`](@ref
