```Julia
irradiance : [FL⁻¹T⁻¹], [FL⁻¹T⁻¹], [MT⁻³], [MT⁻³], [MT⁻³]
irradiance(U::UnitSystem,S::UnitSystem) = power(U,S)/area(U,S)
irradiance(v::Real,U::UnitSystem,S::UnitSystem) = v/irradiance(U,S)
FL⁻¹T⁻¹ [ħ⁻³𝘤⁶mₑ⁴ϕ⁻³g₀⁻⁴] Unified
```

Heat flux density or irradiance or `power` per `area` (W⋅m⁻², kg⋅s⁻³), unit conversion factor.

```Julia
julia> irradiance(CGS,Metric) # kg⋅g⁻¹
2⁻³5⁻³ = 0.001 [N⋅m⁻¹]/[dyn⋅cm⁻¹] Gauss -> Metric

julia> irradiance(CGS,English) # lb⋅g⁻¹
g₀⁻¹ft⋅lb⁻¹2⁻³5⁻³ = 6.852176585679177×10⁻⁵ [lbf⋅ft⁻¹]/[dyn⋅cm⁻¹] Gauss -> English

julia> irradiance(English,Metric) # kg⋅lb⁻¹
g₀⋅ft⁻¹lb = 14.593902937206364 [N⋅m⁻¹]/[lbf⋅ft⁻¹] English -> Metric
```
