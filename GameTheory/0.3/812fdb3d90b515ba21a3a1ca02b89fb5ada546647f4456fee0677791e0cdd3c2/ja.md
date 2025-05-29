```
time_series([rng=Random.GLOBAL_RNG,] ld, ts_length, init_actions)
```

アクションプロファイルの時系列を返します。

# 引数

  * `rng::AbstractRNG` : 使用される乱数生成器。
  * `ld::LogitDynamics{N}` : `LogitDynamics` インスタンス。
  * `ts_length::Integer` : 時系列の長さ。
  * `init_actions::PureActionProfile` : 初期アクションプロファイル。

# 戻り値

  * `::Matrix{<:Integer}` : アクションプロファイルの時系列。
