```
strel_type(x)
```

Infer the structuring element type for `x`.

!!! note "developer note"
    This function is used to dispatch special SE types, e.g., [`SEBoxArray`](@ref), to optimized implementation of particular morphology filter. In this sense it is required for custom SE array types to define this method.

