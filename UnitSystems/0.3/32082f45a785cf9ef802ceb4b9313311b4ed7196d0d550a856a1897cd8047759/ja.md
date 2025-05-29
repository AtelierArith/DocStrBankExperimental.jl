```Julia
jerk(U::UnitSystem,S::UnitSystem) = speed(U,S)/time(U,S)^2
jerk(v::Real,U::UnitSystem,S::UnitSystem) = v/jerk(U,S)
```

ジャークまたは `加速度` あたりの `時間` または `ジャーク` (m⋅s⁻³)、単位変換係数。

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
