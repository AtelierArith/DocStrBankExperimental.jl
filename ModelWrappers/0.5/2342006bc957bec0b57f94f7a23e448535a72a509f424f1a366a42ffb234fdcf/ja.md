```julia
struct Unconstrained{B<:ModelWrappers.Bijection} <: ModelWrappers.AbstractConstraint
```

パラメータに境界を割り当てるのを助けるユーティリティ構造体 - パラメータを制約なしに保つ。パラメータの関数にバッファ値を割り当てるのに便利です。

# フィールド

  * `bijection::ModelWrappers.Bijection`
