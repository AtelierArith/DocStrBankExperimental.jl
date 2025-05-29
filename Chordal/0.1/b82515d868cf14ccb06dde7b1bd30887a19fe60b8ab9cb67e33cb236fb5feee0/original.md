```
sparsity_pattern(mats::AbstractVector{SparseMatrixCSC{T,S}}) where {T, S <: Integer}
```

Returns the 0/1 aggregate sparsity pattern of the matrices in `mats` as a sparse matrix.
