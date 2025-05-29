```
struct StorageValueCuts <: FutureValue
```

複数の `StorageValueCut` のコレクションで、保存された資源の将来価値に対する区分線形上限を構築します。

## フィールド

  * **`id::Any`** は `StorageValueCuts` の名前/識別子です。
  * **`time::Int`** はカットが有効な時間で、運用期間の開始に対して相対的です。
  * **`weight::Real`** は目的関数における `StorageValueCuts` の重み付けです。例えば、最適化の終了時間が異なる2つの `StorageValueCuts` の間に到達する場合に使用されます。
  * **`time_weight::Real`** は経過時間に基づく目的関数における `StorageValueCuts` の重み付けです。
  * **`cuts::Vector{StorageValueCut}`** は将来価値の説明に含まれるすべてのカットのベクターです。
