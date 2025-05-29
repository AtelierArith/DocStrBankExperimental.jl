```
copy_tensor(;
    destination::DafWriter,
    source::DafReader,
    main_axis::AbstractString,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString,
    [rows_reaxis::Maybe{AbstractString} = nothing,
    columns_reaxis::Maybe{AbstractString} = nothing,
    rename::Maybe{AbstractString} = nothing,
    dtype::Maybe{Type{<:StorageScalarBase}} = nothing,
    empty::Maybe{StorageScalar} = nothing,
    relayout::Bool = true,
    overwrite::Bool = false]
)::Nothing
```

Copy a tensor from some `source` [`DafReader`](@ref) into some `destination` [`DafWriter`](@ref).

This is basically a loop that calls [`copy_matrix!`](@ref) for each of the tensor matrices, based on the entries of the `main_axis` in the `destination`. This will create an matrix full of the `empty` value for any entries of the main axis which exist in the destination but do not exist in the source.
