```
mutable struct TimeSeriesTemperature <: Temperature end
```

シミュレーションに使用される温度時系列のデータ（°C）。

# 引数

  * `value::Float64`: °Cでの温度値の時系列。
  * `probability::Float64`: 時系列が観測されると期待される確率。
  * `selected_scenario::Int`
