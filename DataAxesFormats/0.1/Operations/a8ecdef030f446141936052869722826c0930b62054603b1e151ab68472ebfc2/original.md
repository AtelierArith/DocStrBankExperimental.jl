```
float_dtype_for(
    element_type::Type{<:StorageReal},
    dtype::Maybe{Type{<:StorageReal}}
)::Type{<:AbstractFloat}
```

Given an input `element_type`, return the data type to use for the result of an operation that always produces floating point values (e.g., [`Log`](@ref)). If `dtype` isn't  `nothing`, it is returned instead.
