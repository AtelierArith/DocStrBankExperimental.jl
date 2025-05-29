```
anticommute(A::AbstractOperator, B::AbstractOperator)
```

`A`と`B`の反交換を返します。

```jldoctest
julia> σ_x = sigma_x()
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    1.0 + 0.0im    .


julia> anticommute(σ_x, σ_x)
(2,2)-element Snowflurry.DiagonalOperator:
Underlying data type: ComplexF64:
2.0 + 0.0im    .
.    2.0 + 0.0im

```
