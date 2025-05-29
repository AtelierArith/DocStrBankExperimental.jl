```
struct DielectricDistribution{T, N, S, AT} <: AbstractArray{T, N}
```

Dielectric distribution, or distribution of the relative permittivity, $\epsilon_r$,  needed to calculate the [`ElectricPotential`](@ref). The dielectric distribution is unitless.

## Parametric types

  * `T`: Element type of `data`.
  * `N`: Dimension of the `grid` and `data` array.
  * `S`: Coordinate system (`Cartesian` or `Cylindrical`).
  * `AT`: Axes type.

## Fields

  * `data::Array{T, N}`: Array containing the values of the dielectric distribution at the discrete points of the `grid`.
  * `grid::Grid{T, N, S, AT}`: [`Grid`](@ref) defining the discrete points at which the electric potential is determined.

!!! note
    The `data` array contains the values of the dielectric distribution at the discrete points  between the points defined by the axes ticks of the extended grid of `grid`.

    Thus, `size(data) == size(grid) .+ 1` !

