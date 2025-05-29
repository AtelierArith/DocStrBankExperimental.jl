```Julia
snap(U::UnitSystem,S::UnitSystem) = speed(U,S)/time(U,S)^3
snap(v::Real,U::UnitSystem,S::UnitSystem) = v/snap(U,S)
```

ジャウンスまたは `ジャーク` あたりの `時間` または `スナップ` (m⋅s⁻⁴)、単位変換係数。

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
