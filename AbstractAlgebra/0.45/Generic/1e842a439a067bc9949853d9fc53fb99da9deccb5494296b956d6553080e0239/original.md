```
matrix_repr(a::Perm)
```

Return the permutation matrix as a sparse matrix representing `a` via natural embedding of the permutation group into the general linear group over $\mathbb{Z}$.

# Examples

```jldoctest
julia> p = Perm([2,3,1])
(1,2,3)

julia> matrix_repr(p)
3×3 SparseArrays.SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 ⋅  1  ⋅
 ⋅  ⋅  1
 1  ⋅  ⋅

julia> Array(ans)
3×3 Matrix{Int64}:
 0  1  0
 0  0  1
 1  0  0
```
