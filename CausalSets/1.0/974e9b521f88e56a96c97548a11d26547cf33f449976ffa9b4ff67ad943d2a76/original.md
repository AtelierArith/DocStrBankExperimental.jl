```
TimeBoundary{N}(upper_bound::Float64, lower_bound::Float64) <: AbstractBoundary{N}
```

The region for which the proper time as perceived by a still-standing observer at the center of the coordinate system lies between `upper_bound` and `lower_bound`. This notion only makes sense for conformally timesliceable manifolds with compact spacelike slices, so it is only defined for [`HypercylinderManifold`](@ref) and [`DeSitterManifold`](@ref).
