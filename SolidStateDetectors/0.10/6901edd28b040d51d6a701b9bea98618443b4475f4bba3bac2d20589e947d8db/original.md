```
struct ElectricPotential{T, N, S, AT} <: AbstractArray{T, N}
```

Electric potential of the simulation in units of volt (V).

## Parametric types

  * `T`: Element type of `data`.
  * `N`: Dimension of the `grid` and `data` array.
  * `S`: Coordinate system (`Cartesian` or `Cylindrical`).
  * `AT`: Axes type.

## Fields

  * `data::Array{T, N}`: Array containing the values of the electric potential at the discrete points of the `grid`.
  * `grid::Grid{T, N, S, AT}`: [`Grid`](@ref) defining the discrete points for which the electric potential is determined.
