```
DensityReinitializationCallback(; interval::Integer=0, dt=0.0)
```

[`ContinuityDensity`](@ref) [Panizzo2007](@cite) を使用する際に密度フィールドを再初期化するためのコールバックです。

# キーワード

  * `interval=0`:              `interval` タイムステップごとに密度を再初期化します。
  * `dt`:                      積分時間の観点から `dt` の定期的な間隔で密度を再初期化します。
  * `reinit_initial_solution`: 初期解を再初期化します（デフォルトは false）。
