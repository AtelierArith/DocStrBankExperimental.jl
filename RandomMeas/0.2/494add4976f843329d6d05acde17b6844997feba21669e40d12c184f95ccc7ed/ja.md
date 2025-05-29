```
MeasurementGroup(ψ::Union{MPO, MPS}, NU::Int, NM::Int, depth::Int; mode::String = “MPS/MPO”, progress_bar::Bool=false)
```

::MeasurementGroup{ShallowUnitaryMeasurementSetting}

量子状態 `ψ` から `NU` 個の浅い測定設定を生成し、単位行列ごとに `NM` 回の測定をシミュレーションすることによって、MeasurementGroup を構築します。

# 引数

  * `ψ::Union{MPO, MPS}`: 量子状態。
  * `NU::Int`: 生成する測定データオブジェクトの数。
  * `NM::Int`: 設定ごとの測定回数。
  * `depth::Int`: 浅い設定の回路の深さ。
  * `mode::String`: シミュレーションモード; デフォルトは “MPS/MPO”。
  * `progress_bar`::Bool: 進行状況バーを表示するかどうか。

# 戻り値

MeasurementGroup{ShallowUnitaryMeasurementSetting} オブジェクト。
