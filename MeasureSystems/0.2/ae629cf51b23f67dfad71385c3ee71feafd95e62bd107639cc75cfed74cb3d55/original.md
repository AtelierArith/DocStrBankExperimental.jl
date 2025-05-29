```Julia
speed : [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹]
speed(U::UnitSystem,S::UnitSystem) = lightspeed(S)/lightspeed(U)
speed(v::Real,U::UnitSystem,S::UnitSystem) = v/speed(U,S)
LT⁻¹ [𝘤] Unified
```

Velocity or `length` per `time` or `speed` (m⋅s⁻¹), unit conversion factor.

```Julia
julia> speed(CGS,Metric) # m⋅cm⁻¹
2⁻²5⁻² = 0.010000000000000002 [m]/[cm] Gauss -> Metric

julia> speed(IAU,Metric) # m⋅day⋅s⁻¹⋅au⁻¹
au⋅2⁻⁷3⁻³5⁻² = 1.731456836806(35) × 10⁶ [m⋅s⁻¹]/[au⋅D⁻¹] IAU☉ -> Metric

julia> speed(English,Metric) # m⋅ft⁻¹
ft = 0.3048 [m]/[ft] English -> Metric

julia> speed(Survey,English) # ft⋅ftUS⁻¹
ft⁻¹ftUS = 1.0000020000039997 [ft]/[ft] Survey -> English
```
