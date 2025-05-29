```
autocovariance(g⃗, Q::Eigen, timelist; progress=false)
```

可観測量 g⃗ の自己共分散を生成行列 Q と timelist の時刻で計算します。

# 引数

  * `g⃗::AbstractVector`: 可観測量
  * `Q::Eigen`: 生成行列の固有値分解
  * `timelist::AbstractVector`: 自己共分散を計算する時刻

# キーワード引数

  * `progress::Bool=false`: 進行状況バーを表示する

# 戻り値

  * `autocov::Vector`: 可観測量 g⃗ の自己共分散、生成行列 Q と timelist の時刻で
