```
delete_matrix!(
    daf::DafWriter,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString;
    [must_exist::Bool = true,
    relayout::Bool = true]
)::Nothing
```

Delete a matrix property with some `name` for some `rows_axis` and `columns_axis` from `daf`.

If `relayout` (the default), this will also delete the matrix in the other layout (that is, with flipped axes).

This first verifies the `rows_axis` and `columns_axis` exist in `daf`. If `must_exist` (the default), this also verifies the `name` matrix exists for the `rows_axis` and `columns_axis`.
