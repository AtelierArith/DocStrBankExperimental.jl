```Julia
impulse : [FT], [FT], [MLT⁻¹], [MLT⁻¹], [MLT⁻¹]
impulse(U::UnitSystem,S::UnitSystem) = force(U,S)*time(U,S)
impulse(v::Real,U::UnitSystem,S::UnitSystem) = v/impulse(U,S)
FT [𝘤⋅mₑ⋅g₀⁻¹] Unified
```

Linear `impulse` or `force` times `time` (N⋅s, kg⋅m⋅s⁻¹), unit conversion factor.

```Julia
julia> impulse(CGS,Metric) # N⋅dyn⁻¹
2⁻⁵5⁻⁵ = 1.0×10⁻⁵ [N]/[dyn] Gauss -> Metric

julia> impulse(CGS,English) # lb⋅dyn⁻¹
g₀⁻¹lb⁻¹2⁻⁵5⁻⁵ = 2.248089430997105×10⁻⁶ [lbf]/[dyn] Gauss -> English

julia> impulse(English,Metric) # N⋅lb⁻¹
g₀⋅lb = 4.4482216152605 [N]/[lbf] English -> Metric
```
