```Julia
gallon(U::UnitSystem) = volume(𝟕*𝟏𝟏/𝟐^2,U,English)
```

Unit of `volume` derived from the US liquid `gallon` in cubic inches (m³ or ft³).

```Julia
julia> gallon(Metric) # m³
0.003785411784000002

julia> gallon(CGS) # cm³
3785.4117840000026

julia> gallon(IPS) # in³
231
```
