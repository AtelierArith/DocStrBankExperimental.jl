```
scaled_data(sp::ScalingProblem)
scaled_data(sp::ScalingProblem, ps)
```

`ScalingProblem` `sp`のスケーリングデータを返します。

# 引数

  * `sp::ScalingProblem`: スケーリング問題
  * `ps::Vector{Float64}=sp.optimal_ps`: データをスケーリングするためのパラメータ（手動）

# 戻り値

  * `xs::Vector{Vector{Float64}}`: スケーリングされたx値
  * `ys::Vector{Vector{Float64}}`: スケーリングされたy値
  * `es::Vector{Vector{Float64}}`: スケーリングされたy誤差値
  * `Ls::Vector{Float64}`: スケーリングされたシステムサイズ
