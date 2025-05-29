```
function sigma0column(θ,S,p)
σ₀ for a water column
Untested for a mix of float values
```

# 引数

  * `θz::Vector{T}`: 潜在温度
  * `Sz::Vector{T}`: 実用塩分
  * `pz::Vector{T}`: 標準圧力の垂直プロファイル

# 出力

  * `σ₀`: カラム内の湿った点のシグマ-0
