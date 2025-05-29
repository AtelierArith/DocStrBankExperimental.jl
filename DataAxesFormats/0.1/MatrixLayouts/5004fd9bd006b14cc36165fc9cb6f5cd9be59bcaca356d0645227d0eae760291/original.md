```
densify(matrix::AbstractMatrix{T}; copy::Bool = false)::AbstractMatrix{T} where {T <: StorageReal}
densify(vector::AbstractVector{T}; copy::Bool = false)::AbstractVector{T} where {T <: StorageReal}
```

Return a dense version of an array. This will preserve matrix layout. If `copy`, this will create a copy even if it is already dense.
