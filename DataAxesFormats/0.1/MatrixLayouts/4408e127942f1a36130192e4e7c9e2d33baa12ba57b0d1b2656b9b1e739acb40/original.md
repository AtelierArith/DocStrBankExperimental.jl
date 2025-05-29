```
sparsify(matrix::AbstractMatrix{T}; copy::Bool = false)::AbstractMatrix{T} where {T <: StorageReal}
sparsify(vector::AbstractVector{T}; copy::Bool = false)::AbstractVector{T} where {T <: StorageReal}
```

Return a sparse version of an array. This will preserve the matrix layout. If `copy`, this will create a copy even if it is already sparse.
