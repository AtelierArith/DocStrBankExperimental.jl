```
SelectClosest(τ::AbstractFloat; distance::Function = absolute_distance)
```

Incoming cuts are placed into the closest aggregate, according the supplied `distance` function. An empty aggregate is chosen if no aggregate is within the tolerance `τ`

The following distance measures are available

  * [`absolute_distance`](@ref)
  * [`angular_distance`](@ref)
  * [`spatioangular_distance`](@ref
