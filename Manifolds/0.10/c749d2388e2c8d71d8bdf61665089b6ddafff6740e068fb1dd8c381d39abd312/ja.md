```
rand(::MetricManifold{ℝ,<:ProbabilitySimplex,<:EuclideanMetric}; vector_at=nothing, σ::Real=1.0)
```

`vector_at`が`nothing`の場合、独立した指数分布のサンプルを単位和に正規化することによって、ユークリッド計量多様体`M`上の[`ProbabilitySimplex`](@ref)のランダム（均一）点`x`を返します。詳細は[Devroye:1986](@cite)の定理2.1および2.2をそれぞれ207ページと208ページで参照してください。`vector_at`が`nothing`でない場合、標準偏差`σ`を持つ多変量ガウス分布をシフトさせて、ゼロの成分和を持つ（ガウス）ランダムベクトルを接空間$T_{p}\mathrm{\Delta}^n$から返します。
