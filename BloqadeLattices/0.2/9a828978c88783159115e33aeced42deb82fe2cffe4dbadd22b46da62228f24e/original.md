```
dimension(lattice::BoundedLattice{L,C})
```

Returns the dimensions of the `BoundedLattice` (e.g.: `2` for 2D, `3` for 3D)

```jldoctest; setup=:(using BloqadeLattices)
julia> bl = parallelepiped_region(ChainLattice(),(4,);pbc=true) # create a 1D BoundedLattice

julia> dimension(bl)
1

julia> bl = parallelepiped_region(SquareLattice(),(3,0),(0,2);) # create a 2D BoundedLattice

julia> dimension(bl)
2
```
