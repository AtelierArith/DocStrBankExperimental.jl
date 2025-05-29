```
get_factorized_shadows(measurement_data::MeasurementData{LocalUnitaryMeasurementSetting};
                       G::Vector{Float64} = fill(1.0, measurement_data.N))
```

提供された `MeasurementData` のすべての測定結果に対して因子化シャドウを計算します。

# 引数

  * `measurement_data::MeasurementData{LocalUnitaryMeasurementSetting}`: 測定結果と設定を含む測定データオブジェクト。
  * `G::Vector{Float64}` (オプション): 測定誤差補正のための `G` 値のベクトル（デフォルト: すべてのサイトに対して 1.0）。

# 戻り値

次元を持つ NM の `FactorizedShadow` オブジェクトのベクトル。
