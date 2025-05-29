```
NBodyChargeCloud(center::CartesianPoint{T}, energy::T, N::Integer, particle_type::Type{PT} = Gamma; kwargs...)
```

Returns an [`NBodyChargeCloud`](@ref) for a given `energy` deposition at a position that defines the `center` of the charge cloud, given by a center charge surrounded by shells of approximately `N` point charges equally distributed on the surface of a sphere. Find the algorithm to create the shells [here](https://www.cmu.edu/biolphys/deserno/pdf/sphere_equi.pdf).

## Arguments

  * `center::CartesianPoint{T}`: Center position of the [`NBodyChargeCloud`](@ref).
  * `energy::RealQuantity`: Deposited energy with units. If no units are given, the value is parsed in units of eV.
  * `N::Integer`: Approximate number of charges in the [`NBodyChargeCloud`](@ref) (might vary by around 1%).
  * `particle_type`: [`ParticleType`](@ref) of the particle that deposited the energy. Default is `Gamma`.

## Keywords

  * `radius::T`: Estimate for the radius of the [`NBodyChargeCloud`](@ref). Default is determined from `particle_type` via `radius_guess`.
  * `number_of_shells::Int`: Number of shells around the `center` point. Default is `2`.

## Example

```julia
center = CartesianPoint{T}([0,0,0])
energy = 1460u"keV"
NBodyChargeCloud(center, energy, 200, number_of_shells = 3)
```

!!! note
    Using values with units for `energy` requires the package [Unitful.jl](https://github.com/PainterQubits/Unitful.jl).

