```Julia
speed(U::UnitSystem,S::UnitSystem) = lightspeed(S)/lightspeed(U)
speed(v::Real,U::UnitSystem,S::UnitSystem) = v/speed(U,S)
```

速度または `length` あたりの `time` または `speed` (m⋅s⁻¹)、単位変換係数。

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
