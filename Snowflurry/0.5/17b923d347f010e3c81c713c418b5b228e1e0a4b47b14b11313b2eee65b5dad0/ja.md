```
sparse(x::AbstractOperator)
```

xのスパースオペレーター表現を返します。

# 例

```jldoctest
julia> z = sparse(sigma_z())
(2, 2)-element Snowflurry.SparseOperator:
Underlying data ComplexF64:
 1.0 + 0.0im        ⋅     
      ⋅       -1.0 + 0.0im
```
