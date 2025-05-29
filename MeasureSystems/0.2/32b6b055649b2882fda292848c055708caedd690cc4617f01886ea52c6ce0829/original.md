```Julia
action : [FLT], [FLT], [ML²T⁻¹], [ML²T⁻¹], [ML²T⁻¹]
action(U::UnitSystem,S::UnitSystem) = energy(U,S)*time(U,S)
action(v::Real,U::UnitSystem,S::UnitSystem) = v/action(U,S)
FLT [ħ⋅ϕ] Unified
```

Integrated `momentum` over `length` or `action` (J⋅s, N⋅m⋅s), unit conversion factor.

```Julia
julia> action(CGS,Metric) # J⋅erg⁻¹
2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [J]/[erg] Gauss -> Metric

julia> action(CGS,English) # ft⋅lb⋅erg⁻¹
g₀⁻¹ft⁻¹lb⁻¹2⁻⁷5⁻⁷ = 7.375621492772652×10⁻⁸ [lbf⋅ft]/[erg] Gauss -> English

julia> action(English,Metric) # J⋅ft⁻¹⋅lb⁻¹
g₀⋅ft⋅lb = 1.3558179483314003 [J]/[lbf⋅ft] English -> Metric
```
