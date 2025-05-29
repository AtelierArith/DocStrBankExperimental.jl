```Julia
fluence : [FL⁻¹], [FL⁻¹], [MT⁻²], [MT⁻²], [MT⁻²]
fluence(U::UnitSystem,S::UnitSystem) = energy(U,S)/area(U,S
fluence(v::Real,U::UnitSystem,S::UnitSystem) = v/fluence(U,S)
FL⁻¹ [ħ⁻²𝘤⁴mₑ³ϕ⁻²g₀⁻³] Unified
```

Radiant exposure or `force` per `length` or stiffness (N⋅m⁻¹, J⋅m⁻²), unit conversion factor.

```Julia
julia> fluence(CGS,Metric) # kg⋅g⁻¹
2⁻³5⁻³ = 0.001 [kg]/[g] Gauss -> Metric

julia> fluence(CGS,English) # lb⋅g⁻¹
g₀⁻¹ft⋅lb⁻¹2⁻³5⁻³ = 6.852176585679177×10⁻⁵ [lbf⋅ft⁻¹]/[dyn⋅cm⁻¹] Gauss -> English

julia> fluence(CODATA,Metric) # kg⋅kg⁻¹
𝘩⋅RK⋅KJ²2⁻² = 1.000000017(12) [kg]/[kg] CODATA -> Metric

julia> fluence(Conventional,Metric) # kg⋅kg⁻¹
𝘩⋅RK90⋅KJ90²2⁻² = 1.000000195536555 [N]/[N] Conventional -> Metric

julia> fluence(English,Metric) # kg⋅lb⁻¹
g₀⋅ft⁻¹lb = 14.593902937206364 [N⋅m⁻¹]/[lbf⋅ft⁻¹] English -> Metric
```
