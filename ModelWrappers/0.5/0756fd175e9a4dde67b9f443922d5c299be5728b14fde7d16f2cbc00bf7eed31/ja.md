```julia
struct Fixed{B<:ModelWrappers.Bijection} <: ModelWrappers.AbstractConstraint
```

パラメータに境界を割り当てるのを助けるユーティリティ構造体 - パラメータを固定します。パラメータの関数にバッファ値を割り当てるのに便利です。

# フィールド

  * `bijection::ModelWrappers.Bijection`
