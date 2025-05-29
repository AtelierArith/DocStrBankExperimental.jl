```Julia
fluidounce(U::UnitSystem) = cup(U)/𝟐^3
volume : [L³], [L³], [L³], [L³], [L³]
L³⋅(R∞³α⁻⁶ft³τ³2⁻¹⁰3⁻²7⋅11 = 5.1357487905(47) × 10³²) [ħ³𝘤⁻³mₑ⁻³ϕ³g₀³] 統一

English unit of `volume` (m³ or ft³).

```

Julia julia> fluidounce(Metric) # m³ ft³2⁻¹³3⁻²7⋅11 = 2.9573529562499998×10⁻⁵ [m³] メトリック

julia> fluidounce(CGS) # cm³ ft³2⁻⁷3⁻²5⁶7⋅11 = 29.573529562500006 [mL] ガウス

julia> fluidounce(IPS) # in³ 2⁻⁷3⋅7⋅11 = 1.8046875 [in³] IPS ```
