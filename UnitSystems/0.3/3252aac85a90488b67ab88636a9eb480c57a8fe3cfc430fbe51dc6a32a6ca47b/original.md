```Julia
angulartime(U::UnitSystem,S::UnitSystem) = time(U,S)/angle(U,S)
angulartime(v::Real,U::UnitSystem,S::UnitSystem) = v/angulartime(U,S)
```

Circular `time` per `angle` (s⋅rad⁻¹), unit conversion factor.

```Julia
julia> angulartime(IAU,Metric) s⋅day⁻¹
86400.0
```
