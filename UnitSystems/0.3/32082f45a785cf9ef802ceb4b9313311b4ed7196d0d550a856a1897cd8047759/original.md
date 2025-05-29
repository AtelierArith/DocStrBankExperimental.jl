```Julia
jerk(U::UnitSystem,S::UnitSystem) = speed(U,S)/time(U,S)^2
jerk(v::Real,U::UnitSystem,S::UnitSystem) = v/jerk(U,S)
```

Jolt or `acceleration` per `time` or `jerk` (m⋅s⁻³), unit conversion factor.

```Julia
julia> jerk(CGS,Metric) # m⋅cm⁻¹
0.01

julia> jerk(IAU,Metric) # m⋅day³⋅s⁻³⋅au⁻¹
0.00023194455654223942

julia> jerk(English,Metric) # m⋅ft⁻¹
0.3048

julia> jerk(Survey,English) # ft⋅ftUS⁻¹
1.000002000004
```
