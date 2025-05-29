```
NLLSsolver.nvars(var)
```

Return the intrinsic dimensionality (degrees of freedom) of the variable block, `var`. This  positive integer must remain fixed for the duration of the optimization.

Note that the storage size of `var` can be larger than the intrinsic dimensionality. For  example, a 3D rotation has only 3 intrinsic dimensions, but a useful representation is a  9-element 3x3 matrix.

Default implementations of this method exist for types `Number`, `Vector` and  `StaticVector`.

# Example

For a variable type `Rotation3D` that has three dimensions, the user should define the  following function:

```julia
    NLLSsolver.nvars(::Rotation3D) = static(3)
```

!!! tip
    If the dimensionality is known at compile time, return a static integer.


!!! note
    Required user-specialized API function.

