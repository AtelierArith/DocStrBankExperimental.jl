```Julia
power : [FLT⁻¹], [FLT⁻¹], [ML²T⁻³], [ML²T⁻³], [ML²T⁻³]
power(U::UnitSystem,S::UnitSystem) = energy(U,S)/time(U,S))
power(v::Real,U::UnitSystem,S::UnitSystem) = v/power(U,S)
FLT⁻¹ [ħ⁻¹𝘤⁴mₑ²ϕ⁻¹g₀⁻²] Unified
```

Radiant flux or `power` or `energy` per `time` (W, J⋅s⁻¹, kg⋅m²⋅s⁻³), unit conversion factor.

```Julia
julia> power(CGS,Metric) # W⋅s⋅erg⁻¹
2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [J]/[erg] Gauss -> Metric

julia> power(English,Metric) # W⋅s⋅ft⁻¹⋅lb⁻¹
g₀⋅ft⋅lb = 1.3558179483314003 [J]/[lbf⋅ft] English -> Metric
```
