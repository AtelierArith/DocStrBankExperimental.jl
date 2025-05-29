```
AntiDiagonalOperator{N,T<:Complex}<:AbstractOperator
```

反対対角量子 `Operator` を表す構造体（すなわち、要素型 T の複素行列で、非ゼロ要素がすべて交差対角線上にある）。同等の密行列はサイズ NxN になります。

# 例

```jldoctest
julia> AntiDiagonalOperator([1, 2])
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    2.0 + 0.0im    .

```
