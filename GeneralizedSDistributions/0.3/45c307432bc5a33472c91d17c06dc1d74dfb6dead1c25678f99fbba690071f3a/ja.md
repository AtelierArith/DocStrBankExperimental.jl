```
GSDist(dist::UnivariateDistribution, F₀::Real=0.5;
n::Int=21, diff::Function=three_point_midpoint, h::Real=1.0)
```

# 引数

  * `dist::UnivariateDistribution`: 一変量分布。
  * `F₀::Real`: 分布を中心にするための基準分位点。
  * `n::Integer`: 最小二乗フィットに使用する分布上の点の数。
  * `diff::Function`: 勾配近似のための有限差分法の1つ。
  * `h::Real`: diff関数で使用される分母。
