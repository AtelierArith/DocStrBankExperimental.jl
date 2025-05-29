```
play([rng=Random.GLOBAL_RNG,] ld, init_actions[; num_reps=1])
```

`num_reps` 回の反復後の新しいアクションプロファイルを返します。

# 引数

  * `rng::AbstractRNG` : 使用される乱数生成器。
  * `ld::LogitDynamics{N}` : `LogitDynamics` インスタンス。
  * `init_actions::PureActionProfile` : 初期アクションプロファイル。
  * `num_reps::Integer` : 反復の回数。

# 戻り値

  * `::Vector{<:Integer}` : 新しいアクションプロファイル。
