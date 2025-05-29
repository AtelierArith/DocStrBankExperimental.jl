```Julia
radiantintensity : [FLT⁻¹A⁻²], [FLT⁻¹], [ML²T⁻³], [ML²T⁻³], [ML²T⁻³]
radiantintensity(U::UnitSystem,S::UnitSystem) = power(U,S)/solidangle(U,S)
radiantintensity(v::Real,U::UnitSystem,S::UnitSystem) = v/radiantintensity(U,S)
FLT⁻¹A⁻² [ħ⁻¹𝘤⁴mₑ²ϕ⁻³g₀⁻²] Unified
```

Radiant intensity or `power` per `solidangle` (W⋅sr⁻¹, W⋅rad⁻²), unit conversion factor.

```Julia
julia> radiantintensity(CGS,Metric) # W⋅s⋅erg⁻¹
2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [J]/[erg] Gauss -> Metric

julia> radiantintensity(English,Metric) # W⋅s⋅ft⁻¹⋅lb⁻¹
g₀⋅ft⋅lb = 1.3558179483314003 [J]/[lbf⋅ft] English -> Metric
```
