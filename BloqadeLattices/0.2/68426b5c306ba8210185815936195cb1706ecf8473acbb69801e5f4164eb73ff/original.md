```
lattice_vectors(lattice::BoundedLattice{L,C})
```

Returns the underlying Bravais lattice vectors of the `BoundedLattice`

```jldoctest; setup=:(using BloqadeLattices)
julia> bl = parallelepiped_region(SquareLattice(),(3,0),(0,2);) # create a 2D BoundedLattice

julia> lattice_vectors(bl) # lattice vectors used in Bravais Lattice definition of underlying SquareLattice
((1.0, 0.0), (0.0, 1.0))
```
