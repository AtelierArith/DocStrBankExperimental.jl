```
sum_dtype_for(
    element_type::Type{<:StorageReal},
    dtype::Maybe{Type{<:StorageReal}}
)::Type{<:StorageReal}
```

Given an input `element_type`, return the data type to use for the result of an operation that sums many such values values (e.g., [`Sum`](@ref)). If `dtype` isn't `nothing`, it is returned instead.

This keeps floating point and 64-bit types as-is, but increases any small integer types to the matching 32 bit type (e.g., an input type of `UInt8` will have a sum type of `UInt32`).
