```
intensity(process::ContinuousHawkesProcess, data, times)
```

`data`を考慮して、`times`における`process`の強度を計算します。

# 引数

  * `data::Tuple{Vector{Float64},Vector{Int64},Float64}`: イベントのベクター、各イベントに関連付けられたノードのベクター、およびデータサンプルの期間を含むタプル。
  * `times::Vector{Float64}`: プロセスの強度が計算される時間のベクター。

# 戻り値

  * `λ::Vector{Float64}`: `data`と`process`に条件付けられた強度の`len(times)`配列。
