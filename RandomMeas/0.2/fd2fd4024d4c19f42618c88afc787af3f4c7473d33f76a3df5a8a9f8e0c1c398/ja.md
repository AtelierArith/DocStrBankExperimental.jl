```
MeasurementGroup(ψ::Union{MPO, MPS}, NU::Int, NM::Int; mode::String = “MPS/MPO”, progress_bar::Bool=false)
```

::MeasurementGroup{LocalUnitaryMeasurementSetting}

量子状態 `ψ` から MeasurementGroup を構築し、`NU` 個のローカル測定設定を生成し、各設定ごとに `NM` 回の射影測定をシミュレーションします。

# 引数

  * `ψ::Union{MPO, MPS}`: 量子状態。
  * `NU::Int`: 生成する測定データオブジェクトの数。
  * `NM::Int`: 各設定ごとの測定回数。
  * `mode::String`: シミュレーションモード; デフォルトは “MPS/MPO”。
  * `progress_bar::Bool`: 進捗バーを表示するかどうか。

# 戻り値

MeasurementGroup{LocalUnitaryMeasurementSetting} オブジェクト。
