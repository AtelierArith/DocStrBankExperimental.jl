```
empty_dense_matrix!(
    fill::Function,
    daf::DafWriter,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString,
    eltype::Type{<:StorageReal};
    [overwrite::Bool = false]
)::Any
```

Create an empty dense matrix property with some `name` for some `rows_axis` and `columns_axis` in `daf`, pass it to `fill`, and return the result. Since this is Julia, this will be a column-major `matrix`.

The returned matrix will be uninitialized; the caller is expected to `fill` it with values. This saves creating a copy of the matrix before setting it in `daf`, which makes a huge difference when creating matrices on disk (using memory mapping). For this reason, this does not work for strings, as they do not have a fixed size.

This first verifies the `rows_axis` and `columns_axis` exist in `daf`, that the `matrix` is column-major of the appropriate size. If not `overwrite` (the default), this also verifies the `name` matrix does not exist for the `rows_axis` and `columns_axis`.
