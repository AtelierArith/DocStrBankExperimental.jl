```
SparseOperator{T,M,N}
```

is the abstract type inherited by sparse operator types.  Parameter `T` is the type of the elements.  Parameters `M` and `N` are the number of dimensions of the *rows* and of the *columns* respectively.  Sparse operators are a generalization of sparse matrices in the sense that they implement linear mappings which can be applied to `N`-dimensonal arguments to produce `M`-dimensional results (as explained below).  See [`GeneralMatrix`](@ref) for a similar generalization but for *dense* matrices.

See [`CompressedSparseOperator`](@ref) for usage of sparse operators implementing compressed storage formats.
