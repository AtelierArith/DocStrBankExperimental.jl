```
is_hermitian(A::AbstractOperator)
```

演算子 `A` がエルミート（すなわち自己随伴）であるかどうかを判断します。

# 例

```jldoctest
julia> Y = sigma_y()
(2,2)-要素 Snowflurry.AntiDiagonalOperator:
基礎データ型: ComplexF64:
    .    0.0 - 1.0im
    0.0 + 1.0im    .


julia> is_hermitian(Y)
true

julia> P = sigma_p()
(2,2)-要素 Snowflurry.AntiDiagonalOperator:
基礎データ型: ComplexF64:
    .    1.0 + 0.0im
    0.0 + 0.0im    .


julia> is_hermitian(P)
false

```
