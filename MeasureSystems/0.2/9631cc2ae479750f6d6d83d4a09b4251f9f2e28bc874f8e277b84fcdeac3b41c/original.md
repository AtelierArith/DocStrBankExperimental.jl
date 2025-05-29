```Julia
inertance : [ML⁻⁴], [FL⁻⁵T²], [ML⁻⁴], [ML⁻⁴], [ML⁻⁴]
inertance(U::UnitSystem,S::UnitSystem) = mass(U,S)/length(U,S)^4
inertance(v::Real,U::UnitSystem,S::UnitSystem) = v/inertance(U,S)
ML⁻⁴ [ħ⁻⁴𝘤⁴mₑ⁵ϕ⁻⁴g₀⁻⁴] Unified
```

Acoustic mass or `inertance` (kg⋅m⁴, Pa⋅s²⋅m⁻³), unit conversion factor.

```Julia
julia> inertance(CGS,Metric) # kg⋅cm⁴⋅g⁻¹⋅m⁻⁴
2⁵5⁵ = 100000.0 [kg⋅m⁻⁴]/[g⋅cm⁻⁴] Gauss -> Metric

julia> inertance(CGS,English) # slug⋅cm⁴⋅g⁻¹⋅ft⁻⁴
ft⁴lb⁻¹2⁵5⁵ = 1902.804238360888 [lbm⋅ft⁻⁴]/[g⋅cm⁻⁴] Gauss -> English

julia> inertance(English,Metric) # kg⋅ft⁴⋅lb⁻¹⋅m⁻⁴
ft⁻⁴lb = 52.55401369409494 [kg⋅m⁻⁴]/[lbm⋅ft⁻⁴] English -> Metric
```
