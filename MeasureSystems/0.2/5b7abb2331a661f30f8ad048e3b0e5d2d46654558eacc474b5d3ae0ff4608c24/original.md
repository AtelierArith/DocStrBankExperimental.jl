```Julia
surveyacre(U::UnitSystem) = area(𝟐^3*𝟑^2*𝟓*𝟏𝟏^2,U,Survey)
area : [L²], [L²], [L²], [L²], [L²]
L²⋅(R∞²α⁻⁴ftUS²τ²2⁵3²5⋅11² = 2.7138548048(17) × 10²⁸) [ħ²𝘤⁻²mₑ⁻²ϕ²g₀²] Unified
```

Survey unit of land `area` (m² or ft²).

```Julia
julia> surveyacre(Metric) # m²
ftUS²2³3²5⋅11² = 4046.8726098742513 [m²] Metric

julia> surveyacre(English) # ft²
ft⁻²ftUS²2³3²5⋅11² = 43560.174240522705 [ft²] English

julia> surveyacre(Survey) # ftUS²
2³3²5⋅11² = 43560.0 [ft²] Survey
```
