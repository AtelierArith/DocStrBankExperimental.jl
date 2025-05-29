```
SteadyStateReachedCallback(; interval::Integer=0, dt=0.0,
                           interval_size::Integer=10, abstol=1.0e-8, reltol=1.0e-6)
```

時間ステップ間の運動エネルギーの変化が `abstol + reltol * ekin` で指定された閾値を下回ると、統合が終了します。ここで、`ekin` はシミュレーションの総運動エネルギーです。

# キーワード

  * `interval=0`:     `interval` 時間ステップごとに定常状態条件をチェックします。
  * `dt=0.0`:         統合時間の観点から `dt` の定期的な間隔で定常状態条件をチェックし、追加の `tstops` を加えます（これにより解が変わる可能性があります）。
  * `interval_size`:  運動エネルギーの変化が考慮される間隔。`interval_size` は `interval` または `dt` の（整数の）倍数です。
  * `abstol`:         絶対許容誤差。
  * `reltol`:         相対許容誤差。
