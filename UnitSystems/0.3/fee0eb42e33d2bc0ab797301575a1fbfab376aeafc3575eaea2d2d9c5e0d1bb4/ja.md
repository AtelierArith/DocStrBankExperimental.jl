```Julia
length(U::UnitSystem,S::UnitSystem) = action(U,S)*gravityforce(U,S)/mass(U,S)/speed(U,S)
length(v::Real,U::UnitSystem,S::UnitSystem) = v/length(U,S)
```

一次元の形状の範囲または `length` (m)、単位変換係数。

```Julia
julia> length(CGS,Metric) # m⋅cm⁻¹
0.010000000000000002

julia> length(IAU,Metric) # m⋅au⁻¹
1.495978707e11

julia> length(English,Metric) # m⋅ft⁻¹
0.3048

julia> length(Survey,English) # ft⋅ftUS⁻¹
1.000002000004

julia> length(PlanckGauss,Metric) # m⋅ℓP⁻¹
1.6162552789315494e-35
```
