```
vector_version_counter(daf::DafReader, axis::AbstractString, name::AbstractString)::UInt32
```

Return the version number of the vector. This is incremented every time [`set_vector!`](@ref DataAxesFormats.Writers.set_vector!), [`empty_dense_vector!`](@ref DataAxesFormats.Writers.empty_dense_vector!) or [`empty_sparse_vector!`](@ref DataAxesFormats.Writers.empty_sparse_vector!) are called. It is used by interfaces to other programming languages to minimize copying data.

!!! note
    This is purely in-memory per-instance, and **not** a global persistent version counter. That is, the version counter starts at zero even if opening a persistent disk `daf` data set.

