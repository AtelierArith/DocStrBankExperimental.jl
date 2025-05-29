```
get_matrix(op::AbstractOperator)
```

演算子 `op` に関連付けられた `Matrix` を返します。

# 例

```jldoctest
julia> z = sparse(sigma_z())
(2, 2)-要素 Snowflurry.SparseOperator:
基になるデータ ComplexF64:
 1.0 + 0.0im        ⋅     
      ⋅       -1.0 + 0.0im

julia> z_matrix = get_matrix(z)
2×2 Matrix{ComplexF64}:
 1.0+0.0im   0.0+0.0im
 0.0+0.0im  -1.0+0.0im

```
