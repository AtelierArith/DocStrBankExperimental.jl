```Julia
jerk : [LT⁻³], [LT⁻³], [LT⁻³], [LT⁻³], [LT⁻³]
jerk(U::UnitSystem,S::UnitSystem) = speed(U,S)/time(U,S)^2
jerk(v::Real,U::UnitSystem,S::UnitSystem) = v/jerk(U,S)
LT⁻³ [ħ⁻²𝘤⁵mₑ²ϕ⁻²g₀⁻²] Unified
```

Jolt or `acceleration` per `time` or `jerk` (m⋅s⁻³), unit conversion factor.

```Julia
julia> jerk(CGS,Metric) # m⋅cm⁻¹
2⁻²5⁻² = 0.010000000000000002 [m]/[cm] Gauss -> Metric

julia> jerk(IAU,Metric) # m⋅day³⋅s⁻³⋅au⁻¹
au⋅2⁻²¹3⁻⁹5⁻⁶ = 0.0002319445565422(47) [m⋅s⁻³]/[au⋅D⁻³] IAU☉ -> Metric

julia> jerk(English,Metric) # m⋅ft⁻¹
ft = 0.3048 [m]/[ft] English -> Metric

julia> jerk(Survey,English) # ft⋅ftUS⁻¹
ft⁻¹ftUS = 1.0000020000039997 [ft]/[ft] Survey -> English
```
