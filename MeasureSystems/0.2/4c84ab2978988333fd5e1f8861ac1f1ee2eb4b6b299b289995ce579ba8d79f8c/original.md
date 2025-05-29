```Julia
impedance : [FL⁻⁵T], [FL⁻⁵T], [ML⁻⁴T⁻¹], [ML⁻⁴T⁻¹], [ML⁻⁴T⁻¹]
impedance(U::UnitSystem,S::UnitSystem) = specificimpedance(U,S)/area(U,S)
impedance(v::Real,U::UnitSystem,S::UnitSystem) = v/impedance(U,S)
FL⁻⁵T [ħ⁻⁵𝘤⁶mₑ⁶ϕ⁻⁵g₀⁻⁶] Unified
```

Acoustic `impedance` (Rayl⋅m⁻², Pa⋅s⋅m⁻³, kg⋅s⁻¹⋅m⁻⁴), unit conversion factor.

```Julia
julia> impedance(CGS,Metric) # Pa⋅cm³⋅m⁻³⋅Ba⁻¹
2⁵5⁵ = 100000.0 [kg⋅m⁻⁴s⁻²]/[g⋅cm⁻⁴s⁻²] Gauss -> Metric

julia> impedance(English,Metric) # Pa⋅ft⁵⋅m⁻³⋅lb⁻¹
g₀⋅ft⁻⁵lb = 1690.875388429121 [kg⋅m⁻⁴s⁻²]/[lbf⋅ft⁻⁵] English -> Metric
```
