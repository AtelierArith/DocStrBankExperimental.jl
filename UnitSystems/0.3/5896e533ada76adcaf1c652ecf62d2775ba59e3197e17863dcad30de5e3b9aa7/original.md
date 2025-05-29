```Julia
snap(U::UnitSystem,S::UnitSystem) = speed(U,S)/time(U,S)^3
snap(v::Real,U::UnitSystem,S::UnitSystem) = v/snap(U,S)
```

Jounce or `jerk` per `time` or `snap` (m⋅s⁻⁴), unit conversion factor.

```Julia
julia> snap(CGS,Metric) # m⋅cm⁻¹
0.01

julia> snap(IAU,Metric) # m⋅day⁴⋅s⁻⁴⋅au⁻¹
2.6845434784981412e-9

julia> snap(English,Metric) # m⋅ft⁻¹
0.3048

julia> snap(Survey,English) # ft⋅ftUS⁻¹
1.000002000004
```
