```
relayout_matrix!(
    daf::DafWriter,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString;
    [overwrite::Bool = false]
)::Nothing
```

Given a matrix property with some `name` exists (in column-major layout) in `daf` for the `rows_axis` and the `columns_axis`, then [`relayout!`](@ref) it and store the row-major result as well (that is, with flipped axes).

This is useful following calling [`empty_dense_matrix!`](@ref) or [`empty_sparse_matrix!`](@ref) to ensure both layouts of the matrix are stored in `def`. When calling [`set_matrix!`](@ref), it is simpler to just specify (the default) `relayout = true`.

This first verifies the `rows_axis` and `columns_axis` exist in `daf`, and that there is a `name` (column-major) matrix property for them. If not `overwrite` (the default), this also verifies the `name` matrix does not exist for the *flipped* `rows_axis` and `columns_axis`.

!!! note
    A restriction of the way `Daf` stores data is that square data is only stored in one (column-major) layout (e.g., to store a weighted directed graph between cells, you may store an outgoing*weights matrix where each cell's column holds the outgoing weights from the cell to the other cells. In this case you **can't** ask `Daf` to relayout the matrix to row-major order so that each cell's row would be the incoming weights from the other cells. Instead you would need to explicitly store a separate incoming*weights matrix where each cell's column holds the incoming weights).

