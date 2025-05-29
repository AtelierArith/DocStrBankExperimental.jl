```
empty_dense_vector!(
    fill::Function,
    daf::DafWriter,
    axis::AbstractString,
    name::AbstractString,
    eltype::Type{<:StorageReal};
    [overwrite::Bool = false]
)::Any
```

Create an empty dense vector property with some `name` for some `axis` in `daf`, pass it to `fill`, and return the result.

The returned vector will be uninitialized; the caller is expected to `fill` it with values. This saves creating a copy of the vector before setting it in the data, which makes a huge difference when creating vectors on disk (using memory mapping). For this reason, this does not work for strings, as they do not have a fixed size.

This first verifies the `axis` exists in `daf` and that the property name isn't `name`. If not `overwrite` (the default), this also verifies the `name` vector does not exist for the `axis`.
