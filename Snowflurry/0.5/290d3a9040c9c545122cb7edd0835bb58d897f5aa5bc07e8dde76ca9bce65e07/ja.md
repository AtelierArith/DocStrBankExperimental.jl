```
DiagonalOperator{N,T<:Complex}<:AbstractOperator
```

対角量子 `Operator` を表す構造体（すなわち、要素型 T の複素行列で、非ゼロ要素がすべて対角上にある）。対応する密行列はサイズ NxN になります。

# 例

```jldoctest
julia> z = DiagonalOperator([1.0,-1.0])
(2,2)-element Snowflurry.DiagonalOperator:
Underlying data type: ComplexF64:
1.0 + 0.0im    .
.    -1.0 + 0.0im

julia> z = DiagonalOperator([1.0+im,1.0,1.0,0.0-im])
(4,4)-element Snowflurry.DiagonalOperator:
Underlying data type: ComplexF64:
1.0 + 1.0im    .    .    .
.    1.0 + 0.0im    .    .
.    .    1.0 + 0.0im    .
.    .    .    0.0 - 1.0im

```
