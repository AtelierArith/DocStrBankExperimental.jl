```
struct ElectricField{T, N, S, AT} <: AbstractArray{T, N}
```

Electric field of the simulation in units of volt per meter (V/m).

## Parametric types

  * `T`: Element type of `grid.axes`.
  * `N`: Dimension of the `grid` and `data` array.
  * `S`: Coordinate system (`Cartesian` or `Cylindrical`).
  * `AT`: Axes type.

## Fields

  * `data::Array{<:StaticArray{Tuple{N}, T}, N}`: Array containing the field vectors of the electric field at the discrete points of the `grid`.
  * `grid::Grid{T, N, S, AT}`: [`Grid`](@ref) defining the discrete points for which the electric field is determined.
