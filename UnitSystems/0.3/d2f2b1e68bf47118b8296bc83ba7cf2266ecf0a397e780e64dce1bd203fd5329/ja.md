```Julia
acre(U::UnitSystem) = area(𝟐^4*𝟓^4,U,Metric)
```

土地の英単位 `area` (m² または ft²)。

```Julia
julia> acre(Metric) # m²
4046.856422400001

julia> acre(English) # ft²
43560.00000000002

julia> acre(Survey) # ftUS²
43559.82576017427
```
