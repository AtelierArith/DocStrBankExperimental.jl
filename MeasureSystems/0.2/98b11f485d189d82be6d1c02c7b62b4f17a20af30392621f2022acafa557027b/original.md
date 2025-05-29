```Julia
acre(U::UnitSystem) = area(𝟐^4*𝟓^4,U,Metric)
area : [L²], [L²], [L²], [L²], [L²]
L²⋅(R∞²α⁻⁴ft²τ²2⁵3²5⋅11² = 2.7138439494(17) × 10²⁸) [ħ²𝘤⁻²mₑ⁻²ϕ²g₀²] Unified
```

English unit of land `area` (m² or ft²).

```Julia
julia> acre(Metric) # m²
ft²2³3²5⋅11² = 4046.8564224 [m²] Metric

julia> acre(English) # ft²
2³3²5⋅11² = 43560.0 [ft²] English

julia> acre(Survey) # ftUS²
ft²ftUS⁻²2³3²5⋅11² = 43559.82576017426 [ft²] Survey
```
