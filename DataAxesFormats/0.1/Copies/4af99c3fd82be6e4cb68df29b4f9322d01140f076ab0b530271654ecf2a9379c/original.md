```
copy_scalar(;
    destination::DafWriter,
    source::DafReader,
    name::AbstractString,
    [rename::Maybe{AbstractString} = nothing,
    dtype::Maybe{Type{<:StorageScalarBase}} = nothing,
    default::Union{StorageScalar, Nothing, UndefInitializer} = undef,
    overwrite::Bool = false]
)::Nothing
```

Copy a scalar with some `name` from some `source` [`DafReader`](@ref) into some `destination` [`DafWriter`](@ref).

The scalar is fetched using the `name` and the `default`. If `rename` is specified, store the scalar using this new name. If `dtype` is specified, the data is converted to this type. If `overwrite` (not the default), overwrite an existing scalar in the target.
