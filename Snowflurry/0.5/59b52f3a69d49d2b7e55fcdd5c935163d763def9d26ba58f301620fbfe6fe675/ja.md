```
IdentityOperator{N,T<:Complex}<:AbstractOperator
```

要素型 T を持つ恒等量子演算子を表す構造体。この演算子は常にサイズ 2x2 です。

# 例

```jldoctest
julia> IdentityOperator()
(2, 2)-element Snowflurry.IdentityOperator:
Underlying data ComplexF64:
Equivalent DenseOperator:
1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im

```
