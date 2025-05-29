```
GSDist <: ContinuousUnivariateDistribution
```

一様分布を近似するための一般化S分布。

# 引数

  * `F₀`: 参照分位点。
  * `x₀`: 参照分位点での値。
  * `α, g, k, γ`: 一般化S分布のパラメータ
  * `dist`: 基本となる確率分布。
  * `F`: 分布の累積分布関数。
