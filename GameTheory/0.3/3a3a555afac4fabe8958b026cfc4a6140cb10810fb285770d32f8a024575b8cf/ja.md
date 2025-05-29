```
play([rng=Random.GLOBAL_RNG, ]brd, init_action_dist[, options=BROptions(); num_reps=1])
```

`num_reps` 回の反復後のアクション分布を返します

# 引数

  * `rng::AbstractRNG` : 使用される乱数生成器。
  * `brd::AbstractBRD` : `AbstractBRD` インスタンス。
  * `init_action_dist::Vector{<:Integer}` : プレイヤーのアクションの初期分布。
  * `options::BROptions` : `best_response` メソッドのオプション。
  * `num_reps::Integer` : 反復の回数。

# 戻り値

  * `::Vector{<:Integer}` : 反復後のアクション分布。
