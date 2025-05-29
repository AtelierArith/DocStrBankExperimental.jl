```Julia
specificforce : [FM⁻¹], [LT⁻²], [LT⁻²], [LT⁻²], [LT⁻²]
specificforce(U::UnitSystem,S::UnitSystem) = acceleration(U,S)/gravity(U,S)
specificforce(v::Real,U::UnitSystem,S::UnitSystem) = v/specificforce(U,S)
FM⁻¹ [ħ⁻¹𝘤³mₑ⋅ϕ⁻¹g₀⁻²] Unified
```

Weight or `force` per `mass` or `gforce` (N/kg, m⋅s⁻²), unit conversion factor.

```Julia
julia> specificforce(CGS,Metric)
2⁻²5⁻² = 0.010000000000000002 [m⋅s⁻²]/[gal] Gauss -> Metric

julia> specificforce(Engineering,Metric)
g₀ = 9.80665 [N]/[kgf] Engineering -> Metric

julia> specificforce(English,Metric)
g₀ = 9.80665 [m⋅s⁻²]/[g₀] English -> Metric
```
