```
tr(A::AbstractOperator)
```

演算子 `A` のトレースを計算します。

# 例

```jldoctest
julia> I = eye()
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im


julia> trace = tr(I)
2.0 + 0.0im

```
