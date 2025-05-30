```
SparseOperator{N,T<:Complex}<:AbstractOperator
```

スパース（CSR）行列表現を持つ量子演算子を表す構造体で、要素の型は T です。対応する密な行列はサイズ NxN になります。

!!! warning
    `apply_operator()` メソッドはこの演算子タイプには実装されていません。代わりに `DenseOperator` を使用してみてください。


# 例

```jldoctest
julia> z = SparseOperator([-1.0 1.0;0.0 -1.0])
(2, 2)-element Snowflurry.SparseOperator:
Underlying data ComplexF64:
 -1.0 + 0.0im   1.0 + 0.0im
       ⋅       -1.0 + 0.0im

```
