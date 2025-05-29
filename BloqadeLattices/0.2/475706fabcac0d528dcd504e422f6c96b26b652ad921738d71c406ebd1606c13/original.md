```
parallelepiped_region(lattice::AbstractLattice{D},M::Vararg{NTuple{D,Int},D};pbc::Bool=false;scale::Real=1)
```

Create a `BoundedLattice` given an existing lattice and tuples defining a parallelogram/paralelepiped /line segment defined by vectors that are integer multiples of the lattice vectors in `lattice`.

Periodic Boundary Conditions can be enable/disabled via `pbc`. Tuples must be the same length and quantity as the dimensions of the lattice argument.

```jldoctest; setup=:(using BloqadeLattices)
julia> parallelepiped_region(SquareLattice(),(2,0),(0,2);pbc=true);

julia> parallelepiped_region(KagomeLattice(),(2,2),(-2,2));
```
