```
compare_operators(H_0::AbstractOperator, H_1::AbstractOperator)::Bool
```

2つの入力オペレーター間のグローバル位相差を許容して同等性をチェックします。

# 例

```jldoctest
julia> H_0 = z_90()
(2,2)-element Snowflurry.DiagonalOperator:
Underlying data type: ComplexF64:
0.7071067811865476 - 0.7071067811865475im    .
.    0.7071067811865476 + 0.7071067811865475im


julia> H_1 = phase_shift(pi / 2)
(2,2)-element Snowflurry.DiagonalOperator:
Underlying data type: ComplexF64:
1.0 + 0.0im    .
.    6.123233995736766e-17 + 1.0im


julia> compare_operators(H_0, H_1)
true

julia> H_1 *= sigma_x()
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
0.0 + 0.0im    1.0 + 0.0im
6.123233995736766e-17 + 1.0im    0.0 + 0.0im


julia> compare_operators(H_0, H_1) # sigma xを適用した後はもはや同等ではない
false

```
