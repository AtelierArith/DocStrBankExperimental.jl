```
struct EffectiveChargeDensity{T, N, S, AT} <: AbstractArray{T, N}
```

Effective charge density needed to calculate the [`ElectricPotential`](@ref). The effective charge density is the charge density (in C/m³) times the volume of the voxel of the respective grid point (in m³). Thus, the unit of the effective charge density is Coulomb (C).

## Parametric types

  * `T`: Element type of `data`.
  * `N`: Dimension of the `grid` and `data` array.
  * `S`: Coordinate system (`Cartesian` or `Cylindrical`).
  * `AT`: Axes type.

## Fields

  * `data::Array{T, N}`: Array containing the values of the effective charge density at the discrete points of the `grid`.
  * `grid::Grid{T, N, S, AT}`: [`Grid`](@ref) defining the discrete points at which the electric potential is determined.
