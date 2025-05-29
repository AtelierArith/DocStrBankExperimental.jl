```
struct KagomeLattice <: AbstractLattice{2}
```

Type representing 2D Kagome Lattice.

Used as an argument of [`generate_sites`](@ref) function to produce tiling in a Kagome pattern,  with number of site repetitions being specified by additional arguments of [`generate_sites`](@ref). Kagome is a 2D Lattice, so there must be two integer arguments as additional inputs.

# Example

```julia-repl
julia> generate_sites(KagomeLattice(), 3, 3)
27-element AtomList{2, Float64}:
 (0.0, 0.0)
 (0.25, 0.4330127018922193)
 ...
 (3.25, 2.1650635094610964)
 (3.75, 2.1650635094610964)
```

Overriden functions to return lattice vectors and sites exists as  [`lattice_vectors(::KagomeLattice)`](@ref) and [`lattice_sites(::KagomeLattice)`](@ref).
