```
empty_sparse_matrix!(
    fill::Function,
    daf::DafWriter,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString,
    eltype::Type{<:StorageReal},
    nnz::StorageInteger,
    intdype::Maybe{Type{<:StorageInteger}} = nothing;
    [overwrite::Bool = false]
)::Any
```

Create an empty sparse matrix property with some `name` for some `rows_axis` and `columns_axis` in `daf`, pass its parts (`colptr`, `rowval` and `nzval`) to `fill`, and return the result.

If `indtype` is not specified, it is chosen automatically to be the smallest unsigned integer type needed for the matrix.

The returned matrix will be uninitialized; the caller is expected to `fill` its `colptr`, `rowval` and `nzval` vectors. Specifying the `nnz` makes their sizes known in advance, to allow pre-allocating disk space. For this reason, this does not work for strings, as they do not have a fixed size.

This severely restricts the usefulness of this function, because typically `nnz` is only know after fully computing the matrix. Still, in some cases a large sparse matrix is created by concatenating several smaller ones; this function allows doing so directly into the data, avoiding a copy in case of memory-mapped disk formats.

!!! warning
    It is the caller's responsibility to fill the three vectors with valid data. Specifically, you must ensure:

      * `colptr[1] == 1`
      * `colptr[end] == nnz + 1`
      * `colptr[i] <= colptr[i + 1]`
      * for all `j`, for all `i` such that `colptr[j] <= i` and `i + 1 < colptr[j + 1]`, `1 <= rowptr[i] < rowptr[i + 1] <= nrows`


This first verifies the `rows_axis` and `columns_axis` exist in `daf`. If not `overwrite` (the default), this also verifies the `name` matrix does not exist for the `rows_axis` and `columns_axis`.
