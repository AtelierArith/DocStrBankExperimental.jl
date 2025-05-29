```Julia
surveyacre(U::UnitSystem) = area(𝟐^3*𝟑^2*𝟓*𝟏𝟏^2,U,Survey)
```

土地の調査単位 `area` (m² または ft²)。

```Julia
julia> surveyacre(Metric) # m²
4046.8726098742522

julia> surveyacre(English) # ft²
43560.17424052271

julia> surveyacre(Survey) # ftUS²
43560
```
