```
struct HoneycombLattice <: AbstractLattice{2}
```

Type representing 2D Honeycomb Lattice.

Used as an argument of [`generate_sites`](@ref) function to produce tiling in a honeycomb pattern,  with number of site repetitions being specified by additional arguments of [`generate_sites`](@ref). Honeycomb is a 2D Lattice, so there must be two integer arguments as additional inputs.

# Example

```julia-repl
julia> generate_sites(HoneycombLattice(), 5, 5)
50-element AtomList{2, Float64}:
 (0.0, 0.0)
 (0.5, 0.2886751345948129)
...
 (6.0, 3.4641016151377544)
 (6.5, 3.7527767497325675)

```

Overriden functions to return lattice vectors and sites exists as  [`lattice_vectors(::HoneycombLattice)`](@ref) and [`lattice_sites(::HoneycombLattice)`](@ref).
