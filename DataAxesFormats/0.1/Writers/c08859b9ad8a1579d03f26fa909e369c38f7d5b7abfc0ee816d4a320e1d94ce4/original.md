```
set_vector!(
    daf::DafWriter,
    axis::AbstractString,
    name::AbstractString,
    vector::Union{StorageScalar, StorageVector};
    [overwrite::Bool = false]
)::Nothing
```

Set a vector property with some `name` for some `axis` in `daf`.

If the `vector` specified is actually a [`StorageScalar`](@ref), the stored vector is filled with this value.

This first verifies the `axis` exists in `daf`, that the property name isn't `name`, and that the `vector` has the appropriate length. If not `overwrite` (the default), this also verifies the `name` vector does not exist for the `axis`.
