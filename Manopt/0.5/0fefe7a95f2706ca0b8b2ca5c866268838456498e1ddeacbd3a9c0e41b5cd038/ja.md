```
StopWhenLagrangeMultiplierLess <: StoppingCriterion
```

ラグランジュ乗数の停止基準。

現在、これらは[`convex_bundle_method`](@ref)および[`proximal_bundle_method`](@ref)向けに設計されており、ラグランジュ乗数に基づいて近似（部分）勾配 $g$ と誤差推定 $ε$ が計算されます。

`mode=:both` は、[`convex_bundle_method`](@ref) に対して $ε$ と $\lvert g \rvert$ の両方がそれぞれの `tolerance` より小さいことを要求し、[`proximal_bundle_method`](@ref) に対しては $c$ と $\lvert d \rvert$ がそれぞれの `tolerance` より小さいことを要求します。

`mode=:estimate` は、[`convex_bundle_method`](@ref) に対して $-ξ = \lvert g \rvert^2 + ε$ が与えられた `tolerance` より小さいことを要求します。[`proximal_bundle_method`](@ref) に対しては、方程式は $-ν = μ \lvert d \rvert^2 + c$ となります。

# コンストラクタ

```
StopWhenLagrangeMultiplierLess(tolerance=1e-6; mode::Symbol=:estimate, names=nothing)
```

前述の `mode` のいずれかの停止基準を作成します。`mode=:estimate` の場合、tolerance は単一の数値で構いませんが、`mode=:both` の場合は2つの値のベクトルが必要です。ここで、最初のエントリは $ε$ ($c$) のためのトレランスを指定し、2番目は $\lvert g \rvert$ ($\lvert d \rvert$) のためのトレランスを指定します。
