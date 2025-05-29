```Julia
spectralexposure : [FL⁻¹T], [FL⁻¹T], [MT⁻¹], [MT⁻¹], [MT⁻¹]
spectralexposure(U::UnitSystem,S::UnitSystem) = force(U,S)/speed(U,S)
spectralexposure(v::Real,U::UnitSystem,S::UnitSystem) = v/spectralexposure(U,S)
FL⁻¹T [ħ⁻¹𝘤²mₑ²ϕ⁻¹g₀⁻²] Unified
```

Spectral exposure or `fluence` per `frequency` (N⋅s⋅m⁻¹, J⋅s⋅m⁻²), unit conversion factor.

```Julia
julia> spectralexposure(CGS,Metric) # kg⋅g⁻¹
2⁻³5⁻³ = 0.001 [N⋅m⁻¹]/[dyn⋅cm⁻¹] Gauss -> Metric

julia> spectralexposure(CGS,English) # lb⋅g⁻¹
g₀⁻¹ft⋅lb⁻¹2⁻³5⁻³ = 6.852176585679177×10⁻⁵ [lbf⋅ft⁻¹]/[dyn⋅cm⁻¹] Gauss -> English

julia> spectralexposure(CODATA,Metric) # kg⋅kg⁻¹
𝘩⋅RK⋅KJ²2⁻² = 1.000000017(12) [N]/[N] CODATA -> Metric

julia> spectralexposure(Conventional,Metric) # kg⋅kg⁻¹
𝘩⋅RK90⋅KJ90²2⁻² = 1.000000195536555 [N]/[N] Conventional -> Metric

julia> spectralexposure(English,Metric) # kg⋅lb⁻¹
g₀⋅ft⁻¹lb = 14.593902937206364 [N⋅m⁻¹]/[lbf⋅ft⁻¹] English -> Metric
```
