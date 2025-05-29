```
struct RectangularLattice <: AbstractLattice{2}
```

Type representing 2D Rectangular Lattice.

Used as an argument of [`generate_sites`](@ref) function to produce tiling in a Rectangular pattern,  with number of site repetitions being specified by additional arguments of [`generate_sites`](@ref). Rectangular is a 2D Lattice, so there must be two integer arguments as additional inputs. This type also enables the user to modify the length of one of the Bravais lattice vectors,  by passing a single integer on construction as the aspect ratio.

# Example

```julia-repl
julia> generate_sites(RectangularLattice(2.0), 2, 2)
4-element AtomList{2, Float64}:
 (0.0, 0.0)
 (1.0, 0.0)
 (0.0, 2.0)
 (1.0, 2.0)
```

Overriden functions to return lattice vectors and sites exists as  [`lattice_vectors(::RectangularLattice)`](@ref) and [`lattice_sites(::RectangularLattice)`](@ref).
