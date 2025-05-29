```Julia
statutemile(U::UnitSystem) = length(𝟐^5*𝟑*𝟓*𝟏𝟏,U,Survey)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²ftUS⋅τ⋅2⁶3⋅5⋅11 = 4.1675737247(13) × 10¹⁵) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] Unified
```

法令 `Survey` マイル (m または ft)。

```Julia
julia> statutemile(Metric) # m
ftUS⋅2⁵3⋅5⋅11 = 1609.3472186944373 [m] Metric

julia> statutemile(English) # ft
ft⁻¹ftUS⋅2⁵3⋅5⋅11 = 5280.010560021119 [ft] English

julia> statutemile(Survey) # ftUS
2⁵3⋅5⋅11 = 5280.0 [ft] Survey
```
