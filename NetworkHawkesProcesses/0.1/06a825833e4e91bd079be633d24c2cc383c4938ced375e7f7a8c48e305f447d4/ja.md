```
rand(process::ContinuousHawkesProcess, duration)
```

連続ハークス過程からのランダムなイベントシーケンスをサンプリングします。

# 引数

  * `duration::Float64`: サンプルの期間。

# 戻り値

  * `data::Tuple{Vector{Float64},Vector{Int64},Float64}`: イベントのベクター、各イベントに関連付けられたノードのベクター、およびデータサンプルの期間を含むタプル。
