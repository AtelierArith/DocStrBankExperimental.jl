```
partial_trace(shadow::FactorizedShadow, subsystem::Vector{Int}; assume_unit_trace::Bool = false)
```

指定されたサブシステムの補集合に対して `FactorizedShadow` オブジェクトの部分トレースを計算します。

# 引数

  * `shadow::FactorizedShadow`: 部分トレースを計算するためのファクタライズドシャドウ。
  * `subsystem::Vector{Int}`: サブシステムを保持するために指定されたサイトインデックスのベクター（1ベース）。
  * `assume_unit_trace::Bool` (オプション): `true` の場合、すべてのトレースアウトされたテンソルが単位トレースであると仮定し、明示的な計算をスキップします（デフォルト: `false`）。

# 戻り値

指定されたサブシステムに縮小された新しい `FactorizedShadow` オブジェクト。

# 注意事項

  * `assume_unit_trace` が `true` の場合、効率のために明示的なトレース計算を回避します。
  * `assume_unit_trace` が `false` の場合、サブシステムの外側にあるすべてのテンソルのトレースを計算し、それらの積を残りのテンソルに掛け算します。
  * `assume_unit_trace` が `false` の場合、トレースの積が1から大きく逸脱した場合に警告を発します。
