```
autocovariance(x; timesteps=length(x), progress = false)
```

時系列 `x` の自己共分散を `timesteps` のラグで計算します。

# 引数

  * `x::AbstractVector`: 時系列

# キーワード引数

  * `timesteps::Int`: ラグの数
  * `progress::Bool`: 進行状況バーを表示する

# 戻り値

  * `autocov::Vector`: `timesteps` のラグを持つ `x` の自己共分散
