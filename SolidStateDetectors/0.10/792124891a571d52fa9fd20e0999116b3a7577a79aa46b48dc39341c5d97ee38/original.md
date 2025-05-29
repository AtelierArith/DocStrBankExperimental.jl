```
struct WeightingPotential{T, N, S, AT} <: AbstractArray{T, N}
```

Weighting potential for a given [`Contact`](@ref) which is a unitless potential.

## Parametric types

  * `T`: Element type of `data`.
  * `N`: Dimension of the `grid` and `data` array.
  * `S`: Coordinate system (`Cartesian` or `Cylindrical`).
  * `AT`: Axes type.

## Fields

  * `data::Array{T, N}`: Array containing the values of the weighting potential at the discrete points of the `grid`.
  * `grid::Grid{T, N, S, AT}`: [`Grid`](@ref) defining the discrete points for which the weighting potential is determined.
