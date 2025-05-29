```Julia
solarflux(U::UnitSystem) = hecto^2*jansky(U)
fluence : [FL⁻¹], [FL⁻¹], [MT⁻²], [MT⁻²], [MT⁻²]
FL⁻¹⋅(𝘩⁻¹𝘤⁻¹R∞⁻³α⁶τ⁻²2⁻²⁵5⁻²² = 1.8213882206(17) × 10⁻³⁴) [ħ⁻²𝘤⁴mₑ³ϕ⁻²g₀⁻³] Unified
```

Reference unit of spectral irradiance (kg⋅s⁻² or lb⋅ft⁻¹).

```Julia
julia> solarflux(Metric) # kg⋅s⁻²
2⁻²²5⁻²² = 1.0×10⁻²² [N⋅m⁻¹] Metric

julia> solarflux(CGS) # g⋅s⁻²
2⁻¹⁹5⁻¹⁹ = 1.0×10⁻¹⁹ [dyn⋅cm⁻¹] Gauss

julia> solarflux(English) # lb⋅ft⁻¹
g₀⁻¹ft⋅lb⁻¹2⁻²²5⁻²² = 6.852176585679177×10⁻²⁴ [lbf⋅ft⁻¹] English
```
