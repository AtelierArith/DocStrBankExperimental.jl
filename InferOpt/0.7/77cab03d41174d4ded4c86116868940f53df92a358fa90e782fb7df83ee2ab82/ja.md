```
soft_rank(θ::AbstractVector; ε=1.0, rev::Bool=false)
```

ベクトル θ の高速微分可能ランキング。

# 引数

  * `θ`: ソートするベクトル

# キーワード（オプション）引数

  * `ε::Float64=1.0`: 正則化のサイズ
  * `rev::Bool=false`: false の場合は昇順にソート
  * `regularization=:l2`: :l2 の場合は l2 正則化を使用し、:kl の場合は kl 正則化を使用

他に [`soft_rank_l2`](@ref) と [`soft_rank_kl`](@ref) を参照してください。
