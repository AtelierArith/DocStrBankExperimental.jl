```
simulate_record!(eco::Ecosystem, duration::Unitful.Time, interval::Unitful.Time,
     timestep::Unitful.Time)
```

生態系 `eco` を指定された時間の長さ `duration` で実行する関数で、特定のタイムステップ `timestep` と、記録される個体数の時間間隔 `interval` を指定します。オプションとして、生息地のパッチの除去など、全体の生態系が更新されるシナリオも考えられます。
