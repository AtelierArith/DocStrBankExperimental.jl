```Julia
gallon(U::UnitSystem) = volume(𝟕*𝟏𝟏/𝟐^2,U,English)
volume : [L³], [L³], [L³], [L³], [L³]
L³⋅(R∞³α⁻⁶ft³τ³2⁻³3⁻²7⋅11 = 6.5737584518(60) × 10³⁴) [ħ³𝘤⁻³mₑ⁻³ϕ³g₀³] Unified
```

Unit of `volume` derived from the US liquid `gallon` in cubic inches (m³ or ft³).

```Julia
julia> gallon(Metric) # m³
ft³2⁻⁶3⁻²7⋅11 = 0.0037854117839999997 [m³] Metric

julia> gallon(CGS) # cm³
ft³3⁻²5⁶7⋅11 = 3785.411784000001 [mL] Gauss

julia> gallon(IPS) # in³
3⋅7⋅11 = 231.0 [in³] IPS
```
