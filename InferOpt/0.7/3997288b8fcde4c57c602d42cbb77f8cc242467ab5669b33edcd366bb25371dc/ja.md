```julia
struct LinearMaximizer{F, G, H}
```

汎用線形最大化器のラッパーで、形式は argmax_y θᵀg(y) + h(y) です。以下のレイヤーと互換性があります。

  * [`PerturbedAdditive`](@ref) （[`FenchelYoungLoss`](@ref) の有無にかかわらず）
  * [`PerturbedMultiplicative`](@ref) （[`FenchelYoungLoss`](@ref) の有無にかかわらず）
  * [`SPOPlusLoss`](@ref)

# フィールド

  * `maximizer::Any`: 関数 θ ⟼ argmax_y θᵀg(y) + h(y)
  * `g::Any`: 目的に使用される関数 g(y)
  * `h::Any`: 目的に使用される関数 h(y)
