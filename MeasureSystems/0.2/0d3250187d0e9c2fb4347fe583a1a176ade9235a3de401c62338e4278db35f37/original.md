```Julia
acceleration : [LT⁻²], [LT⁻²], [LT⁻²], [LT⁻²], [LT⁻²]
acceleration(U::UnitSystem,S::UnitSystem) = speed(U,S)/time(U,S)
acceleration(v::Real,U::UnitSystem,S::UnitSystem) = v/acceleration(U,S)
LT⁻² [ħ⁻¹𝘤³mₑ⋅ϕ⁻¹g₀⁻¹] Unified
```

Specific force or `speed` per `time` or `acceleration` (m⋅s⁻²), unit conversion factor.

```Julia
julia> acceleration(CGS,Metric) # m⋅s⁻¹⋅gal⁻¹
2⁻²5⁻² = 0.010000000000000002 [m]/[cm] Gauss -> Metric

julia> acceleration(IAU,Metric) # m⋅day²⋅s⁻²⋅au⁻¹
au⋅2⁻¹⁴3⁻⁶5⁻⁴ = 20.0400096852500(40) [m⋅s⁻²]/[au⋅D⁻²] IAU☉ -> Metric

julia> acceleration(English,Metric) # m⋅ft⁻¹
ft = 0.3048 [m]/[ft] English -> Metric

julia> acceleration(Survey,English) # ft⋅ftUS⁻¹
ft⁻¹ftUS = 1.0000020000039997 [ft]/[ft] Survey -> English
```
