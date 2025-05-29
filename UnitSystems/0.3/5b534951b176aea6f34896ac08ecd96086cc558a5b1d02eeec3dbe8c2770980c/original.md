```Julia
specificforce(U::UnitSystem,S::UnitSystem) = acceleration(U,S)/gravity(U,S)
specificforce(v::Real,U::UnitSystem,S::UnitSystem) = v/specificforce(U,S)
```

Weight or `force` per `mass` or `gforce` (N/kg, m⋅s⁻²), unit conversion factor.

```Julia
julia> specificforce(CGS,Metric)
0.01

julia> specificforce(Engineering,Metric)
9.80665

julia> specificforce(English,Metric)
9.80665
```
