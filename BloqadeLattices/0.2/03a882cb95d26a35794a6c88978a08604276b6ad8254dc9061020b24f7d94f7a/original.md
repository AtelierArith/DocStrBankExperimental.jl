```
struct SquareLattice <: AbstractLattice{2}
```

Type representing 2D Square Lattice.

Used as an argument of [`generate_sites`](@ref) function to produce tiling in a square pattern, with number of site repetitions being specified by additional arguments of [`generate_sites`](@ref). Square is a 2D Lattice, so there must be two integer arguments as additional inputs.

# Example

```julia-repl
julia> generate_sites(SquareLattice(), 4, 4)
16-element AtomList{2, Float64}:
 (0.0, 0.0)
 (1.0, 0.0)
 ...
 (2.0, 3.0)
 (3.0, 3.0)

```

Overriden functions to return lattice vectors and sites exists as  [`lattice_vectors(::SquareLattice)`](@ref) and [`lattice_sites(::SquareLattice)`](@ref).
