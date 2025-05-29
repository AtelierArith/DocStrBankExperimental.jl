```
int_dtype_for(
    element_type::Type{<:StorageReal},
    dtype::Maybe{Type{<:StorageReal}}
)::Type{<:Integer}
```

Given an input `element_type`, return the data type to use for the result of an operation that always produces integer values (e.g., [`Round`](@ref)). If `dtype` isn't `nothing`, it is returned instead.
