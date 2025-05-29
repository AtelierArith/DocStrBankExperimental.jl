```Julia
time(U::UnitSystem,S::UnitSystem) = length(U,S)/speed(U,S)
time(v::Real,U::UnitSystem,S::UnitSystem) = v/time(U,S)
```

イベントが順序付けられる次元または `time` (s)、単位変換係数。

```Julia
julia> time(IAU,Metric) # s⋅day⁻¹
86400.0

julia> time(PlanckGauss,Metric) # s⋅tP⁻¹
5.391247297260392e-44
```
