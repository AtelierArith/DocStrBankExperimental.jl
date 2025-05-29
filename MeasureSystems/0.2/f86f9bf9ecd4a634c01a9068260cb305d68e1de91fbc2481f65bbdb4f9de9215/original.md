```Julia
teaspoon(U::UnitSystem) = 𝟓*milli*liter(U)
volume : [L³], [L³], [L³], [L³], [L³]
L³⋅(R∞³α⁻⁶τ³2⁻³5⁻⁵ = 8.6830163097(80) × 10³¹) [ħ³𝘤⁻³mₑ⁻³ϕ³g₀³] Unified
```

Measuring `teaspoon` unit of `volume` (m³ or ft³).

```Julia
julia> teaspoon(Metric) # m³
2⁻⁶5⁻⁵ = 5.0×10⁻⁶ [m³] Metric

julia> teaspoon(CGS) # cm³
5 = 5.0 [mL] Gauss

julia> teaspoon(IPS) # in³
ft⁻³3³5⁻⁵ = 0.3051187204736614 [in³] IPS
```
