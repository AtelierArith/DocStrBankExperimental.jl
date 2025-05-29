```Julia
frequencydrift(U::UnitSystem,S::UnitSystem) = 1/time(U,S)^2
frequencydrift(v::Real,U::UnitSystem,S::UnitSystem) = v/frequencydrift(U,S)
```

Drift of `frequency` per `time` or `frequencydrift` (Hz⋅s⁻¹, s⁻²), unit conversion factor.

```Julia
julia> frequencydrift(IAU,Metric) day²⋅Hz⋅s⁻¹
1.3395919067215363e-10
```
