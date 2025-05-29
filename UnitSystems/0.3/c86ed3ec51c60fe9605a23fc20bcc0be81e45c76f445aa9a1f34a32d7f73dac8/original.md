```Julia
time(U::UnitSystem,S::UnitSystem) = length(U,S)/speed(U,S)
time(v::Real,U::UnitSystem,S::UnitSystem) = v/time(U,S)
```

Dimension along which events are ordered or `time` (s), unit conversion factor.

```Julia
julia> time(IAU,Metric) # s⋅day⁻¹
86400.0

julia> time(PlanckGauss,Metric) # s⋅tP⁻¹
5.391247297260392e-44
```
