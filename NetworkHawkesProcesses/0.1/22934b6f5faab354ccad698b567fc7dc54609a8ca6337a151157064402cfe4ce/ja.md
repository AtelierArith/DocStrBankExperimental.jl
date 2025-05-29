```
loglikelihood(process::ContinuousHawkesProcess, data)
```

`data`の対数尤度を計算します。

# 引数

  * `data::Tuple{Vector{Float64},Vector{Int64},Float64}`: イベントのベクター、各イベントに関連付けられたノードのベクター、およびデータサンプルの期間を含むタプル。
  * `recursive::Bool`: 可能であれば再帰的な定式化を使用します。

# 戻り値

  * `ll::Float64`: データの対数尤度。
