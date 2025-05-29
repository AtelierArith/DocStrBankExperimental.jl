```
autocovariance(g⃗, Ps::Vector{Matrix{Float64}}, steps::Int; progress = false)
```

可観測量 g⃗ の自己共分散を遷移行列 Ps とステップ数で計算します。

# 引数

  * `g⃗::AbstractVector`: 可観測量
  * `Ps::Vector{Matrix{Float64}}`: 遷移行列
  * `steps::Int`: ステップ数

# キーワード引数

  * `progress::Bool=false`: 進行状況バーを表示する

# 戻り値

  * `autocov::Vector`: 遷移行列 Ps とステップ数での可観測量 g⃗ の自己共分散
