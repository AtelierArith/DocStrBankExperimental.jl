```
StorageMatrix{T} = AbstractMatrix{T} where {T <: StorageReal}
```

Matrices that can be directly stored (and fetched) from `Daf` storage.

The element type must be a [`StorageReal`](@ref), to allow efficient storage of the data in disk files. That is, matrices of strings are **not** supported.

!!! note
    All matrices we store must have a clear [`MatrixLayouts`](@ref DataAxesFormats.MatrixLayouts), that is, must be in either row-major or column-major format.

