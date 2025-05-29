```
DenseOperator{N,T<:Complex}<:AbstractOperator
```

サイズ NxN のフル（密）行列表現を持ち、型 T の要素を含む量子演算子を表す構造体です。

# 例

```jldoctest
julia> z = DenseOperator([1.0 0.0;0.0 -1.0])
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    -1.0 + 0.0im

```

または：

```jldoctest
julia> z = rotation(π/2, -π/4)  
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
0.7071067811865476 + 0.0im    0.4999999999999999 - 0.5im
-0.4999999999999999 - 0.5im    0.7071067811865476 + 0.0im


```
