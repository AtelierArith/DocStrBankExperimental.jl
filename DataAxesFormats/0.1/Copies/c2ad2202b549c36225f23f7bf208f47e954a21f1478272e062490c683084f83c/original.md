```
copy_matrix(;
    destination::DafWriter,
    source::DafReader,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString,
    [rows_reaxis::Maybe{AbstractString} = nothing,
    columns_reaxis::Maybe{AbstractString} = nothing,
    rename::Maybe{AbstractString} = nothing,
    dtype::Maybe{Type{<:StorageScalarBase}} = nothing,
    default::Union{StorageScalar, StorageVector, Nothing, UndefInitializer} = undef,
    empty::Maybe{StorageScalar} = nothing,
    relayout::Bool = true,
    overwrite::Bool = false]
)::Nothing
```

Copy a matrix from some `source` [`DafReader`](@ref) into some `destination` [`DafWriter`](@ref).

The matrix is fetched using the `rows_axis`, `columns_axis`, `name`, `relayout` and the `default`. If `rows_reaxis` and/or `columns_reaxis` are specified, store the vector using these axes. If `rename` is specified, store the matrix using this name. If `dtype` is specified, the data is converted to this type. If `overwrite` (not the default), overwrite an existing matrix in the target. The matrix is stored with the same `relayout`.

This requires each axis of one data set is the same, or is a superset of, or a subset of, the other. If a target axis contains entries that do not exist in the source, then `empty` must be specified to fill the missing values. If a source axis contains entries that do not exist in the target, they are discarded (not copied).

!!! note
    When copying a matrix from a subset to a superset, if the `empty` value is zero, then we create a sparse matrix in the destination. However, currently we create a temporary dense matrix for this; this is inefficient and should be replaced by a more efficient method.

