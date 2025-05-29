```Julia
specificity : [L³T⁻¹N⁻¹], [L³T⁻¹N⁻¹], [L³T⁻¹N⁻¹], [L³T⁻¹N⁻¹], [L³T⁻¹N⁻¹]
specificity(U::UnitSystem,S::UnitSystem) = volume(U,S)/molaramount(U,S)/time(U,S)
specificity(v::Real,U::UnitSystem,S::UnitSystem) = v/specificity(U,S)
L³T⁻¹N⁻¹ [ħ²𝘤⁻¹mₑ⁻³Mᵤ⋅ϕ²g₀²] Unified
```

Catalytic efficiency or `volume` per `mole` per `time` (m³⋅mol⁻¹⋅s⁻¹), unit conversion factor.

```Julia
julia> specificity(CGS,Metric) # m³⋅cm⁻³
2⁻⁶5⁻⁶ = 1.0×10⁻⁶ [m³]/[mL] Gauss -> Metric

julia> specificity(English,Metric) # m³⋅lb-mol⋅mol⁻¹⋅ft⁻³
ft³lb⁻¹2⁻³5⁻³ = 6.242796057614462×10⁻⁵ [m³mol⁻¹]/[ft³lb-mol⁻¹] English -> Metric
```
