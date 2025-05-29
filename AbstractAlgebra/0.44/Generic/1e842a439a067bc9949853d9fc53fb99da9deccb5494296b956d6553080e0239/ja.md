```
matrix_repr(a::Perm)
```

順列群を一般線形群への自然埋め込みを介して表すスパース行列として順列行列を返します。

# 例

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
