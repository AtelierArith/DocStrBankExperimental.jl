```
NParticles(lat[, internal], N[; T=0, statistics=FermiDirac, occupations_type])
NParticles(sys, N[; T=0, statistics=FermiDirac, occupations_type])
```

Create a manybody system with a given lattice and a given number of particles.

## Arguments

  * `lat`: the lattice of the system.
  * `internal`: The basis for the internal degrees of freedom.
  * `sys`: a one-particle system.
  * `N`: the number of particles in the system.

## Keyword Arguments

  * `T`: the temperature of the system. Default is `0`.
  * `statistics`: the statistics of the particles. Default is `FermiDirac`.
  * `occupations_type`: The occupations type for the many-body operator. By default, the   occupation numbers are stored in vectors, but you can use, for example, set it to   `FermionBitstring`s for better performance on fermion systems.

## Example

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(3, 3);

julia> NParticles(lat, 4, statistics=BoseEinstein)
NParticles(4 bosons) on 9-site SquareLattice in 2D space
```
