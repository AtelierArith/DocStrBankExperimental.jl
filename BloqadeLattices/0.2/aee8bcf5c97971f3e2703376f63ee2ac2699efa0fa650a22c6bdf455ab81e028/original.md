```
distance(lattice::BoundedLattice,x,y)
```

Returns the distance between two points in the [`BoundedLattice`](@ref). 

Points `x` and `y` can be any iterable and must have the same dimensions as the [`BoundedLattice`](@ref)  (ex: `(x,y)` for a 2D lattice, `(x,y,z)` for a 3D lattice).

If the Periodic Boundary Condition option has been set to `true` for the [`BoundedLattice`](@ref), the smallest distance between points (modulo the region) is returned, otherwise the standard Euclidean metric is used.

```jldoctest; setup=:(using BloqadeLattices)
julia> bl = parallelepiped_region(SquareLattice(), (1,0),(0,1);) # Define 2D BoundedLattice

julia> distance(bl, (0.1, 0.1), (0.5, 1.1)) # distance between two points
1.077032961426901

julia> bl_pbc = parallelepiped_region(SquareLattice(), (1,0),(0,1);pbc=true) # Define 2D BoundedLattice with Periodic Boundary Condition

julia> distance(bl_pbc, (0.1, 0.1), (0.5, 1.1)) # distance with periodic boundary condition enabled
0.4
```
