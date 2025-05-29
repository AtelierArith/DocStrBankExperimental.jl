```
lattice_sites(lattice::BoundedLattice{L,C})
```

Returns the underlying site vectors that define the unit-cell of the `BoundedLattice`

```jldoctest; setup=:(using BloqadeLattices)
julia> bl = parallelepiped_region(SquareLattice(),(3,0),(0,2);) # create a 2D BoundedLattice

julia> lattice_sites(bl) # lattice vectors used in Bravais Lattice definition of underlying SquareLattice
((0.0, 0.0), )
```
