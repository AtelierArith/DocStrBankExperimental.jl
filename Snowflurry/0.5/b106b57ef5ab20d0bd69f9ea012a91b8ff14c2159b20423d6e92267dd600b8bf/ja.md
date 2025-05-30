```
SwapLikeOperator{N,T<:Complex}<:AbstractOperator
```

量子演算子を表す構造体で、「スワップ」操作を実行し、要素タイプ T を持ちます。スワップされたキュービットの係数には `phase` 値が適用されます。この演算子は常に 4x4 のサイズです。

例えば、`phase=0.0 + 1.0im` を使用して iswap `Operator` を構築するには、次のように呼び出します。

```jldoctest
julia> SwapLikeOperator(0.0 + 1.0im)
(4, 4)-element Snowflurry.SwapLikeOperator:
Underlying data ComplexF64:
Equivalent DenseOperator:
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 1.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 1.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im

```
