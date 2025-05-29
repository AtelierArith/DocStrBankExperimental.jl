```
get_dense_shadows(measurement_group::MeasurementGroup{LocalUnitaryMeasurementSetting};
                  G::Vector{Float64} = fill(1.0, N),
                  number_of_ru_batches::Int = NU)
```

提供された測定データの密なシャドウをバッチで計算します。

# 引数

  * `measurement_group::MeasurementGroup{LocalUnitaryMeasurementSetting}`: 測定データオブジェクト。
  * `G::Vector{Float64}` (オプション): ロバスト性のためのG値のベクトル（デフォルト: すべてのサイトに対して1.0）。
  * `number_of_ru_batches::Int` (オプション): ランダムユニタリバッチの数（デフォルト: `NU`）。

# 戻り値

`DenseShadow`オブジェクトのベクトル。
