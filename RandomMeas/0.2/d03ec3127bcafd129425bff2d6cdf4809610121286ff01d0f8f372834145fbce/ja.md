```
MeasurementGroup(ψ::Union{MPO, MPS}, measurement_settings::Vector{AbstractMeasurementSetting}, NM::Int; mode::String = “MPS/MPO”, progress_bar::Bool=false)
::MeasurementGroup{T} where T <: AbstractMeasurementSetting
```

量子状態 `ψ` から MeasurementGroup を構築し、`NU` のローカル測定設定を生成し、設定ごとに `NM` の射影測定をシミュレーションします。

# 引数

  * `ψ::Union{MPO, MPS}`: 量子状態。
  * `measurement_settings::Vector{AbstractMeasurementSetting}`: 測定設定のベクトル
  * `NM::Int`: 設定ごとの測定回数。
  * `mode::String`: シミュレーションモード; デフォルトは “MPS/MPO”。
  * `progress_bar::Bool`: 進行状況バーを表示するかどうか。

# 戻り値

MeasurementGroup{T} オブジェクト。
