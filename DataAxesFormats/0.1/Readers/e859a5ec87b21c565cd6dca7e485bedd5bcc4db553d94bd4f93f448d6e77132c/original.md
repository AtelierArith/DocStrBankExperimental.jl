```
matrix_version_counter(
    daf::DafReader,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString
)::UInt32
```

Return the version number of the matrix. The order of the axes does not matter. This is incremented every time [`set_matrix!`](@ref DataAxesFormats.Writers.set_matrix!), [`empty_dense_matrix!`](@ref DataAxesFormats.Writers.empty_dense_matrix!) or [`empty_sparse_matrix!`](@ref DataAxesFormats.Writers.empty_sparse_matrix!) are called. It is used by interfaces to other programming languages to minimize copying data.

!!! note
    This is purely in-memory per-instance, and **not** a global persistent version counter. That is, the version counter starts at zero even if opening a persistent disk `daf` data set.

