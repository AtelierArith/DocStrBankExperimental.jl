```
allocate_matrix(sp::SparsityPattern)
```

Allocate a sparse matrix of type `SparseMatrixCSC{Float64, Int}` from the sparsity pattern `sp`.

This method is a shorthand for the equivalent [`allocate_matrix(SparseMatrixCSC{Float64, Int}, sp)`](@ref allocate_matrix(::Type{S}, sp::Ferrite.AbstractSparsityPattern) where {Tv, Ti, S <: SparseMatrixCSC{Tv, Ti}}).
