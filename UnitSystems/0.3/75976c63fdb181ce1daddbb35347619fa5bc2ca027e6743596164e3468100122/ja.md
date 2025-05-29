```Julia
acceleration(U::UnitSystem,S::UnitSystem) = speed(U,S)/time(U,S)
acceleration(v::Real,U::UnitSystem,S::UnitSystem) = v/acceleration(U,S)
```

特定の力または `speed` あたりの `time` または `acceleration` (m⋅s⁻²)、単位変換係数。

```Julia
julia> acceleration(CGS,Metric) # m⋅s⁻¹⋅gal⁻¹
0.01

julia> acceleration(IAU,Metric) # m⋅day²⋅s⁻²⋅au⁻¹
20.040009685249483

julia> acceleration(English,Metric) # m⋅ft⁻¹
0.3048

julia> acceleration(Survey,English) # ft⋅ftUS⁻¹
1.000002000004
```
