```julia
mutable struct SparseMatrixCSB{Tv, Ti} <: SparseArrays.AbstractSparseArray{Tv, Ti, 2}
```

Matrix type for storing sparse matrices in the Compressed Sparse Blocks format. The standard way of constructing `SparseMatrixCSB` is to pass a `SparseMatrixCSC` object, see the constructors.
