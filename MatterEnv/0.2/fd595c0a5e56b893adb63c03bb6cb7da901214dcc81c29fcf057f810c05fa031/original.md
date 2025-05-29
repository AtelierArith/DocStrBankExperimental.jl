```
generate_dos(bands::Bands, kpoints::Array{KPoint, 1},
    projection::Projection;
    smear::Function=gaussian, energy_number::Integer=10000,
    ions::Array{Integer, 1}=nothing, orbits::Array{Integer, 1}=nothing)
```

Generate projected electronic density of states using bands and kpoints.

# Arguments

  * `bands::Bands`: metadata of bands
  * `kpoints::Array{KPoint, 1}`: metadata of k-points
  * `projection::Projection`: metadata of projection
  * `smear::Function=gaussian`: smearing function, default: Gaussian smear
  * `energy_number::Integer=10000`: number of energy points, default 10000
  * `ions::Union{Array{<:Integer, 1}, UnitRange{<:Integer}, Nothing}=nothing`:   index of ions which wavefunction is projected to
  * `orbits::Union{Array{<:Integer, 1}, UnitRange{<:Integer}, Nothing}=nothing`:   index of orbitss which wavefunction is projected to

# Returns

  * `pdos::DOS`: metadata of projected dos
