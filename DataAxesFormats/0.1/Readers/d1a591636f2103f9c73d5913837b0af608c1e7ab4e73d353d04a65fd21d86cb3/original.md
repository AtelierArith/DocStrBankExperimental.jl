```
has_matrix(
    daf::DafReader,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString;
    [relayout::Bool = true]
)::Bool
```

Check whether a matrix property with some `name` exists for the `rows_axis` and the `columns_axis` in `daf`. Since this is Julia, this means a column-major matrix. A daf may contain two copies of the same data, in which case it would report the matrix under both axis orders.

If `relayout` (the default), this will also check whether the data exists in the other layout (that is, with flipped axes).

This first verifies the `rows_axis` and `columns_axis` exists in `daf`.
