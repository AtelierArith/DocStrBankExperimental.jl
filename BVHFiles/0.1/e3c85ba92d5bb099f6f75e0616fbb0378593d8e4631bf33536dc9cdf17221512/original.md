```
project!(g::BVHGraph, h::BVHGraph, T::Matrix = Matrix(1.0I, 3, 3))
```

Transfer the rotations of each vertex in `h` to the corresponding vertex in `g`.  The corresponding vertices must have the same names.  `T` is a rotation matrix that should be provided if the global orientations of `g` and `h` differ.

See also: [`replace_offset!`](@ref), [`replace_offsets!`](@ref)
