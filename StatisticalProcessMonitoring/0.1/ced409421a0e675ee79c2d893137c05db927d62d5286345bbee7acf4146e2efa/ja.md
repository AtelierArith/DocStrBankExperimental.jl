```
TRAS{F,D}
```

# フィールド

部分的な観測を伴う複数のデータストリームを監視するためのTop-rベースの適応サンプリング監視統計。

## フィールド

  * `k::Float64`: CUSUM統計の許容定数。デフォルトは`0.1`。
  * `mu_min::Float64`: 検出されるべき最小シフト。デフォルトは`1.0`。
  * `value::Float64`: 監視統計の現在の値。デフォルトは`0.0`。
  * `Δ::Float64`: 観測されていない変数の補償係数。
  * `r::Int`: 合計する最大の変数の数。
  * `q::Int`: 観測可能な変数の総数。
  * `p::Int`: 変数の総数。
  * `W::Vector{Float64}`: ローカル監視統計のベクトル。デフォルトはゼロのベクトル。
  * `W1::Vector{Float64}`: 平均の増加を検出するためにローカル監視統計を保存するために使用されるベクトル。デフォルトはゼロのベクトル。
  * `W2::Vector{Float64}`: 平均の減少を検出するためにローカル監視統計を保存するために使用されるベクトル。デフォルトはゼロのベクトル。
  * `obs::Vector{Int}`: ローカル監視統計の上位`q`値の選択されたインデックス。デフォルトは範囲`1:p`からのサイズ`q`のランダムサンプル。
  * `sampler::S`: 次の`obs`インデックスのセットを選択するために使用されるサンプリング戦略。デフォルトは`ThompsonSampling()`。

# 参考文献

Liu, K., Mei, Y., & Shi, J. (2015). An Adaptive Sampling Strategy for Online High-Dimensional Process Monitoring. Technometrics, 57(3), 305-319. https://doi.org/10.1080/00401706.2014.947005
