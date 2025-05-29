```
loglikelihood(process::DiscreteHawkesProcess, data)
loglikelihood(process::DiscreteHawkesProcess, data, convolved)
```

`data`の対数尤度を計算します。`convolved`を提供すると、畳み込みステップの計算をスキップします。

# 引数

  * `data::Array{Int64,2}`: `N x T` のイベントカウントの配列。
  * `convolved::Array{Float64,3}`: 基底関数で畳み込まれたイベントカウントの `T x N x B` の配列。

# 戻り値

  * `ll::Float64`: イベントカウントの対数尤度。
