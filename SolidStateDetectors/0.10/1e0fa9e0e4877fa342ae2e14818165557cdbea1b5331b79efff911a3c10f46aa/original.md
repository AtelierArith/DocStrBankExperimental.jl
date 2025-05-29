```
NBodyChargeCloud(center::CartesianPoint{T}, energy::T, particle_type::Type{PT} = Gamma; kwargs...)
```

Returns an [`NBodyChargeCloud`](@ref) for a given `energy` deposition at a position that defines the `center` of the charge cloud, given by a center charge surrounded by shells consisting of platonic solids.

## Arguments

  * `center::CartesianPoint{T}`: Center position of the [`NBodyChargeCloud`](@ref).
  * `energy::RealQuantity`: Deposited energy with units. If no units are given, the value is parsed in units of eV.
  * `particle_type`: [`ParticleType`](@ref) of the particle that deposited the energy. Default is `Gamma`.

## Keywords

  * `radius::T`: Estimate for the radius of the [`NBodyChargeCloud`](@ref). Default is determined from `particle_type` via `radius_guess`.
  * `number_of_shells::Int`: Number of shells around the `center` point. Default is `2`.
  * `shell_structure`: Geometry with which the charges are distributed in the shells. Default is `Dodecahedron`.

## Example

```julia
center = CartesianPoint{T}([0,0,0])
energy = 1460u"keV"
NBodyChargeCloud(center, energy, number_of_shells = 3, shell_structure = SolidStateDetectors.Icosahedron)
```

!!! note
    Using values with units for `energy` requires the package [Unitful.jl](https://github.com/PainterQubits/Unitful.jl).

