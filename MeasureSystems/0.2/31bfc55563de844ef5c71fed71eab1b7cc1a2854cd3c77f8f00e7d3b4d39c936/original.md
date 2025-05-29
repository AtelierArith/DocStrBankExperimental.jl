```Julia
cup(U::UnitSystem) = pint(U)/𝟐
volume : [L³], [L³], [L³], [L³], [L³]
L³⋅(R∞³α⁻⁶ft³τ³2⁻⁷3⁻²7⋅11 = 4.1085990324(38) × 10³³) [ħ³𝘤⁻³mₑ⁻³ϕ³g₀³] Unified
```

English unit of `volume` (m³ or ft³).

```Julia
julia> cup(Metric) # m³
ft³2⁻¹⁰3⁻²7⋅11 = 0.00023658823649999998 [m³] Metric

julia> cup(CGS) # cm³
ft³2⁻⁴3⁻²5⁶7⋅11 = 236.58823650000005 [mL] Gauss

julia> cup(IPS) # in³
2⁻⁴3⋅7⋅11 = 14.4375 [in³] IPS
```
