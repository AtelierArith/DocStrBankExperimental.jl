```
struct ChainLattice <: AbstractLattice{1}
```

Type representing 1D Chain Lattice.

Used as an argument of [`generate_sites`](@ref) function to produce tiling in a chain pattern,  with number of site repetitions being specified by the additional argument of [`generate_sites`](@ref). Chain is a 1D Lattice, so there must be one integer argument as additional inputs.

# Example

```julia-repl
julia> generate_sites(ChainLattice(), 5)
5-element AtomList{1, Float64}:
 (0.0,)
 (1.0,)
 (2.0,)
 (3.0,)
 (4.0,)
```

Overriden functions to return lattice vectors and sites exists as  [`lattice_vectors(::ChainLattice)`](@ref) and [`lattice_sites(::ChainLattice)`](@ref).
