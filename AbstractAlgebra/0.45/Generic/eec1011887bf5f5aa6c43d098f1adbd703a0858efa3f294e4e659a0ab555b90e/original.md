```
matrix_repr(Y::YoungTableau)
```

Construct sparse integer matrix representing the tableau.

# Examples

```jldoctest
julia> y = YoungTableau([4,3,1]);


julia> matrix_repr(y)
3×4 SparseArrays.SparseMatrixCSC{Int64, Int64} with 8 stored entries:
 1  2  3  4
 5  6  7  ⋅
 8  ⋅  ⋅  ⋅
```
