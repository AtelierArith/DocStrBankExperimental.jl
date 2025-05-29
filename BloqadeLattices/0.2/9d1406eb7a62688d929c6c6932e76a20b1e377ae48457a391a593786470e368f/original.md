```
struct TriangularLattice <: AbstractLattice{2}
```

Type representing 2D Square Lattice.

Used as an argument of [`generate_sites`](@ref) function to produce tiling in a triangle pattern,  with number of site repetitions being specified by additional arguments of [`generate_sites`](@ref). Triangle is a 2D Lattice, so there must be two integer arguments as additional inputs.

# Example

```julia-repl
julia> generate_sites(TriangularLattice(), 3, 3)
9-element AtomList{2, Float64}:
 (0.0, 0.0)
 (1.0, 0.0)
 ...
 (2.0, 1.7320508075688772)
 (3.0, 1.7320508075688772)

```

Overriden functions to return lattice vectors and sites exists as  [`lattice_vectors(::TriangularLattice)`](@ref) and [`lattice_sites(::TriangularLattice)`](@ref).
