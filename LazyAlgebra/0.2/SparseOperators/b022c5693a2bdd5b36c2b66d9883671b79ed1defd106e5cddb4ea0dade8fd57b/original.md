Sparse operators in *Compressed Sparse Row* (CSR) format store the significant entries in a row-wise order, as a vector of values, a vector of corresponding linear column indices and a vector of offsets indicating, for each row, the range of indices in the vectors of values and of column indices.  This storage format is very suitable for fast application of the operator.

A sparse operator in CSR storage format can be constructed by providing all necessary information:

```
SparseOperatorCSR(vals, cols, offs, rowsiz, colsiz)
```

where `vals` is the vector of values of the sparse entries, `cols` is an integer valued vector of the linear column indices of the sparse entries, `offs` is a column-wise table of offsets in these arrays, `rowsiz` and `colsiz` are the sizes of the row and column dimensions.  The entries values and respective linear column indices of the `i`-th row are given by `vals[k]` and `cols[k]` with `k ∈ offs[i]+1:offs[i+1]`.  The linear row index `i` is in the range `1:m` where `m = prod(rowsiz)` is the equivalent number of rows.  For efficiency reasons, sparse operators are currently limited to *fast* arrays because they can be indexed linearly with no loss of performances.  If `vals`, `cols` and/or `offs` are not fast arrays, they will be automatically converted to linearly indexed arrays.

A sparse operator in CSR storage format can be directly constructed from a 2-dimensional Julia array `A`:

```
SparseOperatorCSR(A, sel = (v,i,j) -> (v != zero(v)))
```

where optional argument `sel` is a selector function which is called as `sel(v,i,j)` with `v`, `i` and `j` the value, the row and the column linear indices for each entries of `A` and which is assumed to yield `true` for the entries of `A` to be selected in the sparse structure and `false` for the entries of `A` to discard.  The default selector is such that all non-zeros of `A` are selected.

The element type, say `T`, for the sparse coefficients can be imposed by rewriting the above examples as:

```
SparseOperatorCSR{T}(args...)
```

A sparse operator in CSR storage format implementing generalized matrix-vector multiplication can also be directly constructed from a `L`-dimensional Julia array (with `L ≥ 2`) `A` by:

```
SparseOperatorCSR{T,M}(A[, sel])
```

with `M` the number of leading dimensions of `A` corresponding to the *rows* of the operator, the trailing `N = L - M` dimensions being assumed to correspond to the *columns* of the operator.  These dimensions are the size of, respectively, the output and the input arrays when applying the operator.  The parameter `N` may be specified (although it can be automatically determined):

```
SparseOperatorCSR{T,M,N}(A[, sel])
```

provided the equality `M + N = ndims(A)` holds.

A last parameter `V` can be specified for the type of the vector to store the coefficients of the sparse operator:

```
SparseOperatorCSR{T,M,N,V}(args...)
```

provided `V` implements standard linear indexing.  The default is to take `V = Vector{T}`.  As a special case, you can choose a uniform boolean vector from the `StructuredArrays` package to store the sparse coefficients:

```
SparseOperatorCSR{T,M,N,UniformVector{Bool}}(args...)
```

to get a compressed sparse operator in CSR format whose values are an immutable uniform vector of true values requiring no storage.  This is useful to only store the sparse structure of the operator, that is the indices in CSR format of the sparse coefficients not their values.

The `SparseOperatorCSR` constructor can also be used to convert a sparse operator in another storage format into the CSR format.  In that case, parameter `T` may also be specified to convert the type of the sparse coefficients.
