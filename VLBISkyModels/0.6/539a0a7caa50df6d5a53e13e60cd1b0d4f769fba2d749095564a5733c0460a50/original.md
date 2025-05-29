```
PoincareSphere2Map(I, p, X, grid)
PoincareSphere2Map(I::IntensityMap, p, X)
PoincareSphere2Map(I, p, X, cache::AbstractCache)
```

Constructs an polarized intensity map model using the Poincare parameterization. The arguments are:

  * `I` is a grid of fluxes for each pixel.
  * `p` is a grid of numbers between 0, 1 and the represent the total fractional polarization
  * `X` is a grid, where each element is 3 numbers that represents the point on the Poincare sphere that is, X[1,1] is a NTuple{3} such that `||X[1,1]|| == 1`.
  * `grid` is the dimensional grid that gives the pixels locations of the intensity map.

!!! note
    If `I` is an `IntensityMap` then grid is not required since the same grid that was use for `I` will be used to construct the polarized intensity map. If a cache is passed instead this will return a [`ContinuousImage`](@ref) object.

