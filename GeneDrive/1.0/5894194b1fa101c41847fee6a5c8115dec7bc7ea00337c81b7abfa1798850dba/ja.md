```
mutable struct ScenarioTemperature <: Temperature end
```

シミュレーションに使用される温度時系列のアンサンブルデータ（°C）。

# 引数

  * `data::Matrix{Float64}`: アンサンブルメンバーの配列で、各列は° Cの温度値の時系列です。
  * `probability::Vector{Float64}`: 与えられたシナリオが発生することが期待される確率のベクトル（各アンサンブルメンバーに適用される1つの確率）。
  * `selected_scenario::Int`: 選択されたシナリオに対して動的モデルを実行するためのインデックス；`Int`引数が必要です。意思決定モデルの場合は、`nothing`を使用します。
