```
System(lat[, internal; T, μ, N, statistics])
```

Create a system with a given lattice and optionally internal degrees of freedom.

## Arguments

  * `lat`: the lattice of the system.
  * `internal`: The basis for the internal degrees of freedom.

## Keyword Arguments

  * `T`: the temperature of the system. Default is `0`.
  * `μ`: the chemical potential of the system. Use `mu` synonym if Unicode input is not available.
  * `N`: the number of particles in the system.
  * `statistics`: the statistics of the particles. Default is `FermiDirac`.

## Example

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(3, 3);

julia> System(lat)
One particle on 9-site SquareLattice in 2D space

julia> System(lat, N=4, statistics=BoseEinstein)
4 non-interacting bosons on 9-site SquareLattice in 2D space

julia> System(lat, mu=0, statistics=BoseEinstein)
Non-interactng bosons with fixed μ=0.0 on 9-site SquareLattice in 2D space
```
