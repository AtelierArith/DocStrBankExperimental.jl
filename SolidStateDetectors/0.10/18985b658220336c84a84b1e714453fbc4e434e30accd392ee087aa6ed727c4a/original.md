```
struct PointTypes{T, N, S, AT} <: AbstractArray{T, N}
```

Information about the grid points used to calculate the [`ElectricPotential`](@ref) stored via bit-flags. Data is stored as [`PointType`](@ref) which is an `UInt8`.

## Parametric types

  * `T`: Element type of `grid.axes`.
  * `N`: Dimension of the `grid` and `data` array.
  * `S`: Coordinate system (`Cartesian` or `Cylindrical`).
  * `AT`: Axes type.

## Fields

  * `data::Array{PointType, N}`: Array containing the point type values at the discrete points of the `grid`.
  * `grid::Grid{T, N, S, AT}`: [`Grid`](@ref) defining the discrete points for which the point types are determined.

See also [`PointType`](@ref).
