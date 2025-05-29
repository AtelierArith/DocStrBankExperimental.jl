```
simulate_record_diversity!(storage::AbstractArray, eco::Ecosystem,
  times::Unitful.Time, interval::Unitful.Time,timestep::Unitful.Time,
  scenario::SimpleScenario, divfun::Function, qs::Float64)
```

指定された時間の長さ `duration` にわたって生態系 `eco` を実行する関数で、特定のタイムステップ `timestep` と多様性を計算して記録するための時間間隔 `interval` を指定します。オプションとして、生息地のパッチの除去など、全体の生態系が更新されるシナリオも含まれる場合があります。
