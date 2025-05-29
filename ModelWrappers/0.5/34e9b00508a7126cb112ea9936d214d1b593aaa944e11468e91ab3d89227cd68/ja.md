```julia
struct Constrained{B<:ModelWrappers.Bijection} <: ModelWrappers.AbstractConstraint
```

パラメータに境界を割り当てるのを助けるユーティリティ構造体 - スカラー パラメータを制約します。

# フィールド

  * `bijection::ModelWrappers.Bijection`
