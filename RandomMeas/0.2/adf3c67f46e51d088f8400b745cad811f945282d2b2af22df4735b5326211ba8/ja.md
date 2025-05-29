```
MeasurementData(ψ::Union{MPO, MPS}, NM::Int; mode::String = "MPS/MPO", measurement_setting::Union{LocalUnitaryMeasurementSetting, ComputationalBasisMeasurementSetting, ShallowUnitaryMeasurementSetting} = nothing)
```

量子状態 `ψ` から `NM` の射影測定をサンプリングすることによって `MeasurementData` オブジェクトを返します。

# 引数

  * `ψ::Union{MPO, MPS}`: 行列積演算子 (MPO) または行列積状態 (MPS) として表される量子状態。
  * `NM::Int`: 各設定のためにシミュレートする測定ショットの数。
  * `mode::String` (オプション): シミュレーション方法を指定します。オプション:

      * `"dense"`: 密な表現を使用します。
      * `"MPS/MPO"` (デフォルト): メモリ効率のためにテンソルネットワーク手法を使用します。
  * `measurement_setting` (オプション): 測定設定オブジェクト (提供されない場合は計算基底測定がデフォルト)。

# 返り値

対応する測定結果と設定を持つ `MeasurementData` オブジェクト。
