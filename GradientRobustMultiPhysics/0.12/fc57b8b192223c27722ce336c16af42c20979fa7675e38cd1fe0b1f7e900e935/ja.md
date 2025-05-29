```julia
abstract type IdentityDisc{DT<:GradientRobustMultiPhysics.DiscontinuityTreatment} <: id
```

アイデンティティジャンプ演算子: 有限要素関数の面ジャンプを評価します。
