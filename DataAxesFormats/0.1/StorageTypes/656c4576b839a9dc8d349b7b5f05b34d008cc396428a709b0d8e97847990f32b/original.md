```
StorageVector{T} = AbstractVector{T} where {T <: StorageScalar}
```

Vectors that can be directly stored (and fetched) from `Daf` storage.

The element type must be a [`StorageScalar`](@ref), to allow storing the data in disk files. Vectors of strings are supported but will be less efficient.
