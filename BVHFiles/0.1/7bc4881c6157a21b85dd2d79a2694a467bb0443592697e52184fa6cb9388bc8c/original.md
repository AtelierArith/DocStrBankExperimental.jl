```
replace_offset!(g::BVHGraph, h::BVHGraph, gv₊₁::Integer, T::Matrix{Float64} = Matrix(1.0I, 3, 3); change_rotation::Bool = true)
```

Replace the offset of a vertex `gv₊₁` in `g` with the offset of the corresponding vertex in `h`.  The corresponding vertex and its inneighbor must have the same names as those in `g`.  The rotations of the surrounding vertices are adjusted.  `T` is a rotation matrix that should be provided if the global orientations of `g` and `h` differ.

See also: [`replace_offsets!`](@ref), [`project!`](@ref)
