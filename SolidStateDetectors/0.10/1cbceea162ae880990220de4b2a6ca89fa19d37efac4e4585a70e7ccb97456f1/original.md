```
struct Grid{T, N, S <: AbstractCoordinateSystem, AT} <: AbstractGrid{T, N}
```

Collection of `N` axes that define the dimensions of the grid needed to calculate  [`ElectricPotential`](@ref), [`ElectricField`](@ref) or [`WeightingPotential`](@ref).

## Parametric types

  * `T`: Tick type (element type) of the axes.
  * `N`: Dimension of the grid.
  * `S`: Coordinate system (`Cartesian` or `Cylindrical`).
  * `AT`: Axes type.

## Fields

  * `axes::AT`: Tuple of length `N` containing `DiscreteAxis` for each dimension of the grid.

See also [`DiscreteAxis`](@ref).
