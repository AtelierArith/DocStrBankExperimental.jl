```Julia
hectare(U::UnitSystem) = area(hecto^2,U,Metric)
```

土地の面積のメトリック単位 `area` は `100` 平方メートル (m² または ft²) で定義されています。

```Julia
julia> hectare(Metric) # m²
10000

julia> hectare(English) # ft²
107639.10416709722

julia> hectare(Survey) # ftUS²
107638.67361111108
```
