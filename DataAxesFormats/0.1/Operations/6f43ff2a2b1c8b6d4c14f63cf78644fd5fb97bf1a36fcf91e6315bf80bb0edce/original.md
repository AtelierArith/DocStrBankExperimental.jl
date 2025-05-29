```
unsigned_dtype_for(
    element_type::Type{<:StorageReal},
    dtype::Maybe{Type{<:StorageReal}}
)::Type
```

Given an input `element_type`, return the data type to use for the result of an operation that discards the sign of the value (e.g., [`Abs`](@ref)). If `dtype` isn't `nothing`, it is returned instead.
