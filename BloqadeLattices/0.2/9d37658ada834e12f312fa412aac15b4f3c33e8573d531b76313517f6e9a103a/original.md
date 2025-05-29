```
struct LiebLattice <: AbstractLattice{2}
```

Type representing 2D Lieb Lattice.

Used as an argument of [`generate_sites`](@ref) function to produce tiling in a Lieb (square-depleted) pattern,  with number of site repetitions being specified by additional arguments of [`generate_sites`](@ref). Lieb is a 2D Lattice, so there must be two integer arguments as additional inputs.

# Example

```julia-repl
julia> generate_sites(LiebLattice(), 3, 3)
27-element AtomList{2, Float64}:
 (0.0, 0.0)
 (0.5, 0.0)
...
 (2.5, 2.0)
 (2.0, 2.5)
```

Overriden functions to return lattice vectors and sites exists as  [`lattice_vectors(::LiebLattice)`](@ref) and [`lattice_sites(::LiebLattice)`](@ref).
