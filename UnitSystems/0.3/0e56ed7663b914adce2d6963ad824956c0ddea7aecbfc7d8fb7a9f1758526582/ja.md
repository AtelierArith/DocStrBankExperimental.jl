```Julia
gallon(U::UnitSystem) = volume(𝟕*𝟏𝟏/𝟐^2,U,English)
```

米国液体の`gallon`から導出された`volume`の単位は立方インチ（m³またはft³）です。

```Julia
julia> gallon(Metric) # m³
0.003785411784000002

julia> gallon(CGS) # cm³
3785.4117840000026

julia> gallon(IPS) # in³
231
```
