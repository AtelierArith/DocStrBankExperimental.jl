```julia
struct GeneratorStatusRT <: FullNetworkSystems.GeneratorStatus
```

リアルタイムの定式化に必要な発電機の状態時系列データ。

フィールド:

  * `commitment::AxisKeys.KeyedArray{Bool, 2}`: `Bool` で示される発電機のコミットメント状態
  * `regulation_commitment::AxisKeys.KeyedArray{Bool, 2}`: `Bool` で示される発電機の調整コミットメント状態
