```
replace_offsets!(g::BVHGraph, h::BVHGraph, exclude::Vector, T::Matrix{Float64} = Matrix(1.0I, 3, 3))
```

Replace the offsets of all vertices in `g`, except those in `exclude`, with the offsets of  their corresponding vertices in `h`. The corresponding vertex and its inneighbor must have the same names as those in `g`.  The rotations of the surrounding vertices are adjusted.  `T` is a rotation matrix that should be provided if the global orientations of `g` and `h` differ.

See also: [`replace_offset!`](@ref), [`project!`](@ref)
