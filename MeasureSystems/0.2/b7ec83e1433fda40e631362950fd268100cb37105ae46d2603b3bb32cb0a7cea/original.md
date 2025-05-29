```Julia
powerdensity : [FL⁻²T⁻¹], [FL⁻²T⁻¹], [ML⁻¹T⁻³], [ML⁻¹T⁻³], [ML⁻¹T⁻³]
powerdensity(U::UnitSystem,S::UnitSystem) = power(U,S)/volume(U,S)
powerdensity(v::Real,U::UnitSystem,S::UnitSystem) = v/powerdensity(U,S)
FL⁻²T⁻¹ [ħ⁻⁴𝘤⁷mₑ⁵ϕ⁻⁴g₀⁻⁵] Unified
```

Spectral irradiance (volume) or `powerdensity` (W⋅m⁻³), unit conversion factor.

```Julia
julia> powerdensity(CGS,Metric) # kg⋅cm⋅g⁻¹⋅m⁻¹
2⁻¹5⁻¹ = 0.1 [Pa]/[Ba] Gauss -> Metric

julia> powerdensity(CGS,English) # lb⋅cm⋅g⁻¹⋅ft⁻¹
g₀⁻¹ft²lb⁻¹2⁻¹5⁻¹ = 0.002088543423315013 [lbf⋅ft⁻²]/[Ba] Gauss -> English

julia> powerdensity(English,Metric) # kg⋅ft⋅lb⁻¹⋅m⁻¹
g₀⋅ft⁻²lb = 47.88025898033583 [Pa]/[lbf⋅ft⁻²] English -> Metric
```
