```
set_matrix!(
    daf::DafWriter,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString,
    matrix::Union{StorageReal, StorageMatrix};
    [overwrite::Bool = false,
    relayout::Bool = true]
)::Nothing
```

Set the matrix property with some `name` for some `rows_axis` and `columns_axis` in `daf`. Since this is Julia, this should be a column-major `matrix`.

If the `matrix` specified is actually a [`StorageScalar`](@ref), the stored matrix is filled with this value.

If `relayout` (the default), this will also automatically [`relayout!`](@ref) the matrix and store the result, so the data would also be stored in row-major layout (that is, with the axes flipped), similarly to calling [`relayout_matrix!`](@ref).

This first verifies the `rows_axis` and `columns_axis` exist in `daf`, that the `matrix` is column-major of the appropriate size. If not `overwrite` (the default), this also verifies the `name` matrix does not exist for the `rows_axis` and `columns_axis`.
