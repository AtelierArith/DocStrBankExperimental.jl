```
bestify(
    matrix::AbstractMatrix{T};
    copy::Bool = false,
    sparse_if_saves_storage_fraction::AbstractFloat = 0.25,
)::AbstractMatrix{T} where {T <: StorageReal}
bestify(
    matrix::AbstractVector{T};
    copy::Bool = false,
    sparse_if_saves_storage_fraction::AbstractFloat = 0.25,
)::AbstractVector{T} where {T <: StorageReal}
```

Return a "best" (dense or sparse) version of an array. The sparse format is chosen if it saves at least `sparse_if_saves_storage_fraction` of the storage of the dense format. If `copy`, this will create a copy even if it is already in the best format.

!!! note
    If not `copy` and the matrix is already sparse, we do not change the integer index type, even though this may save space.

