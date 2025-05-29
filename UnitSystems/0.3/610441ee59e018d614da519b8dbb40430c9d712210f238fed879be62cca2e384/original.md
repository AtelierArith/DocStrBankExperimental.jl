```Julia
hectare(U::UnitSystem) = area(hecto^2,U,Metric)
```

Metric unit of land `area` defined by `100` square meters (m² or ft²).

```Julia
julia> hectare(Metric) # m²
10000

julia> hectare(English) # ft²
107639.10416709722

julia> hectare(Survey) # ftUS²
107638.67361111108
```
