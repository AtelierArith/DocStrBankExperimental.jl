```
copy_vector(;
    destination::DafWriter,
    source::DafReader,
    axis::AbstractString,
    name::AbstractString,
    [reaxis::Maybe{AbstractString} = nothing,
    rename::Maybe{AbstractString} = nothing,
    dtype::Maybe{Type{<:StorageScalarBase}} = nothing,
    default::Union{StorageScalar, StorageVector, Nothing, UndefInitializer} = undef,
    empty::Maybe{StorageScalar} = nothing,
    overwrite::Bool = false]
)::Nothing
```

Copy a vector from some `source` [`DafReader`](@ref) into some `destination` [`DafWriter`](@ref).

The vector is fetched using the `axis`, `name` and the `default`. If `reaxis` is specified, store the vector using this axis. If `rename` is specified, store the vector using this name. If `dtype` is specified, the data is converted to this type. If `overwrite` (not the default), overwrite an existing vector in the target.

This requires the axis of one data set is the same, or is a superset of, or a subset of, the other. If the target axis contains entries that do not exist in the source, then `empty` must be specified to fill the missing values. If the source axis contains entries that do not exist in the target, they are discarded (not copied).
