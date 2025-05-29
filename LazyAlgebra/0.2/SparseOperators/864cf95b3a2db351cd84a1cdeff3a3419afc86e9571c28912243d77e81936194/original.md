Sparse operators in *Compressed Sparse Coordinate* (COO) format store the significant entries in no particular order, as a vector of values, a vector of linear row indices and a vector of linear column indices.  It is even possible to have repeated entries.  This format is very useful to build a sparse linear operator.  It can be converted to a more efficient format like *Compressed Sparse Column* (CSC) or *Compressed Sparse Row* (CSR) for fast application of the sparse linear mapping or of its adjoint.

A sparse operator in COO storage format can be constructed by providing all necessary information:

```
SparseOperatorCOO(vals, rows, cols, rowsiz, colsiz)
```

where `vals` is the vector of values of the sparse entries, `rows` and `cols` are integer valued vectors with the linear row and column indices of the sparse entries, `rowsiz` and `colsiz` are the sizes of the row and column dimensions. The entries values and respective linear row and column indices of the `k`-th sparse entry are given by `vals[k]`, `rows[k]` and `cols[k]`.  For efficiency reasons, sparse operators are currently limited to *fast* arrays because they can be indexed linearly with no loss of performances.  If `vals`, `rows` and/or `cols` are not fast arrays, they will be automatically converted to linearly indexed arrays.

A sparse operator in COO storage format can be directly constructed from a 2-dimensional Julia array `A`:

```
SparseOperatorCOO(A, sel = (v,i,j) -> (v != zero(v)))
```

where optional argument `sel` is a selector function which is called as `sel(v,i,j)` with `v`, `i` and `j` the value, the row and the column linear indices for each entries of `A` and which is assumed to yield `true` for the entries of `A` to be selected in the sparse structure and `false` for the entries of `A` to discard.  The default selector is such that all non-zeros of `A` are selected.

The element type, say `T`, for the sparse coefficients can be imposed by rewriting the above examples as:

```
SparseOperatorCOO{T}(args...)
```

A sparse operator in COO storage format implementing generalized matrix-vector multiplication can also be directly constructed from a `L`-dimensional Julia array (with `L ≥ 2`) `A` by:

```
SparseOperatorCOO{T,M}(A[, sel])
```

with `M` the number of leading dimensions of `A` corresponding to the *rows* of the operator, the trailing `N = L - M` dimensions being assumed to correspond to the *columns* of the operator.  These dimensions are the size of, respectively, the output and the input arrays when applying the operator.  The parameter `N` may be specified (although it can be automatically determined):

```
SparseOperatorCOO{T,M,N}(A[, sel])
```

provided the equality `M + N = ndims(A)` holds.

A last parameter `V` can be specified for the type of the vector to store the coefficients of the sparse operator:

```
SparseOperatorCOO{T,M,N,V}(args...)
```

provided `V` implements standard linear indexing.  The default is to take `V = Vector{T}`.  As a special case, you can choose a uniform boolean vector from the `StructuredArrays` package to store the sparse coefficients:

```
SparseOperatorCOO{T,M,N,UniformVector{Bool}}(args...)
```

to get a compressed sparse operator in COO format whose values are an immutable uniform vector of true values requiring no storage.  This is useful to only store the sparse structure of the operator, that is the indices in COO format of the sparse coefficients not their values.

The `SparseOperatorCOO` constructor can also be used to convert a sparse operator in another storage format into the COO format.  In that case, parameter `T` may also be specified to convert the type of the sparse coefficients.
