```Julia
frequencydrift(U::UnitSystem,S::UnitSystem) = 1/time(U,S)^2
frequencydrift(v::Real,U::UnitSystem,S::UnitSystem) = v/frequencydrift(U,S)
```

`frequency` の `time` あたりのドリフトまたは `frequencydrift` (Hz⋅s⁻¹, s⁻²)、単位変換係数。

```Julia
julia> frequencydrift(IAU,Metric) day²⋅Hz⋅s⁻¹
1.3395919067215363e-10
```
