```
matrices_set(
    daf::DafReader,
    rows_axis::AbstractString,
    columns_axis::AbstractString;
    [relayout::Bool = true]
)::AbstractSet{<:AbstractString}
```

The names of the matrix properties for the `rows_axis` and `columns_axis` in `daf`.

If `relayout` (default), then this will include the names of matrices that exist in the other layout (that is, with flipped axes).

This first verifies the `rows_axis` and `columns_axis` exist in `daf`.

!!! note
    There's no immutable set type in Julia for us to return. If you do modify the result set, bad things *will* happen.

