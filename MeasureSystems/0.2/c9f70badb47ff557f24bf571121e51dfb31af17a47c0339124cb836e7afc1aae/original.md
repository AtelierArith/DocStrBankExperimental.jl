```Julia
snap : [LT⁻⁴], [LT⁻⁴], [LT⁻⁴], [LT⁻⁴], [LT⁻⁴]
snap(U::UnitSystem,S::UnitSystem) = speed(U,S)/time(U,S)^3
snap(v::Real,U::UnitSystem,S::UnitSystem) = v/snap(U,S)
LT⁻⁴ [ħ⁻³𝘤⁷mₑ³ϕ⁻³g₀⁻³] Unified
```

Jounce or `jerk` per `time` or `snap` (m⋅s⁻⁴), unit conversion factor.

```Julia
julia> snap(CGS,Metric) # m⋅cm⁻¹
2⁻²5⁻² = 0.010000000000000002 [m]/[cm] Gauss -> Metric

julia> snap(IAU,Metric) # m⋅day⁴⋅s⁻⁴⋅au⁻¹
au⋅2⁻²⁸3⁻¹²5⁻⁸ = 2.684543478498(54) × 10⁻⁹ [m⋅s⁻⁴]/[au⋅D⁻⁴] IAU☉ -> Metric

julia> snap(English,Metric) # m⋅ft⁻¹
ft = 0.3048 [m]/[ft] English -> Metric

julia> snap(Survey,English) # ft⋅ftUS⁻¹
ft⁻¹ftUS = 1.0000020000039997 [ft]/[ft] Survey -> English
```
