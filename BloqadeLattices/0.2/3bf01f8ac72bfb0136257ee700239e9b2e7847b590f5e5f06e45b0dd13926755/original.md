```
BoundedLattice(lattice::AbstractLattice{D},region::AbstractRegion{D},pbc::Bool=false)
```

Creates a [`BoundedLattice`](@ref) instance when provided with the underlying `lattice` and `region` to  bound on the lattice, with the option to enable Periodic Boundary Conditions.

See also: [`parallelepiped_region`](@ref)
