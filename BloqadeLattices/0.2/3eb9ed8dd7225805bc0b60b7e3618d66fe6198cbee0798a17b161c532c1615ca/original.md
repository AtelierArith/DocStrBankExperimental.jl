```
struct BoundedLattice{L<:AbstractLattice, R<:AbstractRegion}
```

Defines a lattice bounded by a region with the option for periodic boundary conditions.

# Fields

  * `lattice <: AbstractLattice`: Lattice to be bounded.
  * `region <: AbstractRegion`: Region that bounds the underlying `lattice`.
  * `site_positions::AtomList`: Positions of the atoms inside `region`.
  * `pbc::Bool`: Enable/Disable behavior for Periodic Boundary Conditions.
