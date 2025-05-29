```
get_temperature_value(temperature_model::ScenarioTemperature, temp_value_from_inputs::Float64, t)
```

選択したシナリオと指定された時間ステップに対する温度の値を°Cで返します。適用可能な場合、基準温度への摂動は、モデルを実行する前に時系列に直接追加する必要があります。
