```
minrank_completion(A::SparseMatrixCSC{Tv, Ti}) where {Tv <: AbstractFloat, Ti <: Integer}
```

Returns the cholesky factor of the minimum rank completion (`A_complete = Y*Yᵀ`) of chordal sparse matrix `A` using Algorithm 2 in [Sun15]. This algorithm uses the supernodal elimination tree of `A` and, therefore, BLAS level 3 operations.

# Reference

[Sun15] [Decomposition Methods for Semidefinite Optimization (PhD Thesis)](https://escholarship.org/content/qt1cv6981p/qt1cv6981p.pdf) by Yifan Sun
