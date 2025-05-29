```Julia
speed(U::UnitSystem,S::UnitSystem) = lightspeed(S)/lightspeed(U)
speed(v::Real,U::UnitSystem,S::UnitSystem) = v/speed(U,S)
```

Velocity or `length` per `time` or `speed` (m⋅s⁻¹), unit conversion factor.

```Julia
julia> speed(CGS,Metric) # m⋅cm⁻¹
0.01

julia> speed(IAU,Metric) # m⋅day⋅s⁻¹⋅au⁻¹
1.7314568368055555e6

julia> speed(English,Metric) # m⋅ft⁻¹
0.3048

julia> speed(Survey,English) # ft⋅ftUS⁻¹
1.000002000004
```
