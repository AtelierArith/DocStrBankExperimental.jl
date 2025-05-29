```Julia
spectralflux : [FT⁻¹], [FT⁻¹], [MLT⁻³], [MLT⁻³], [MLT⁻³]
spectralflux(U::UnitSystem,S::UnitSystem) = power(U,S)/length(U,S)
spectralflux(v::Real,U::UnitSystem,S::UnitSystem) = v/spectralflux(U,S)
FT⁻¹ [ħ⁻²𝘤⁵mₑ³ϕ⁻²g₀⁻³] Unified
```

Spectral power or `power` per wave `length` (W⋅m⁻¹), unit conversion factor.

```Julia
julia> spectralflux(CGS,Metric) # kg⋅m⋅g⁻¹⋅cm⁻¹
2⁻⁵5⁻⁵ = 1.0×10⁻⁵ [N]/[dyn] Gauss -> Metric

julia> spectralflux(CGS,English) # lb⋅ft⋅g⁻¹⋅cm⁻¹
g₀⁻¹lb⁻¹2⁻⁵5⁻⁵ = 2.248089430997105×10⁻⁶ [lbf]/[dyn] Gauss -> English

julia> spectralflux(English,Metric) # kg⋅m⋅lb⁻¹⋅ft⁻¹
g₀⋅lb = 4.4482216152605 [N]/[lbf] English -> Metric
```
