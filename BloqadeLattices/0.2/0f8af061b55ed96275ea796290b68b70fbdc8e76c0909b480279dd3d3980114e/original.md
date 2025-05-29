```
Parallelepiped(vecs)
Parallelepiped(vecs::T) where {T<:Real}
```

Define a region (either a line segment, parallelogram, or parallelepiped depending on the dimensions of `vecs`) using a single value or column vectors in a matrix that can be used to create a [`BoundedLattice`](@ref).

```jldoctest; setup=:(using BloqadeLattices)
julia> Parallelepiped(2.0) # can bound a 1D lattice
Parallelepiped{1, Float64}([2.0;;], [0.5;;])

julia> bounds = zeros((2,2)); # Create 2x2 matrix to store vectors defining 2D region

julia> bounds[:,1] .= (3,3); bounds[:,2] .= (4,0); # Column Vectors define the Parallelogram

julia> Parallelepiped(bounds)
Parallelepiped{2, Float64}([3.0 4.0; 3.0 0.0], [0.0 0.3333333333333333; 0.25 -0.25])
```
