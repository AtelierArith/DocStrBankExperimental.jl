```Julia
pint(U::UnitSystem) = quart(U)/𝟐
volume : [L³], [L³], [L³], [L³], [L³]
L³⋅(R∞³α⁻⁶ft³τ³2⁻⁶3⁻²7⋅11 = 8.2171980648(76) × 10³³) [ħ³𝘤⁻³mₑ⁻³ϕ³g₀³] Unified
```

English unit of `volume` (m³ or ft³).

```Julia
julia> pint(Metric) # m³
ft³2⁻⁹3⁻²7⋅11 = 0.00047317647299999996 [m³] Metric

julia> pint(CGS) # cm³
ft³2⁻³3⁻²5⁶7⋅11 = 473.1764730000001 [mL] Gauss

julia> pint(IPS) # in³
2⁻³3⋅7⋅11 = 28.875 [in³] IPS
```
