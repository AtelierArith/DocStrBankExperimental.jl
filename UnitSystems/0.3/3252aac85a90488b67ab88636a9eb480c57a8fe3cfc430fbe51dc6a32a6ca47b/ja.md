```Julia
angulartime(U::UnitSystem,S::UnitSystem) = time(U,S)/angle(U,S)
angulartime(v::Real,U::UnitSystem,S::UnitSystem) = v/angulartime(U,S)
```

円周の `time` あたりの `angle` (s⋅rad⁻¹)、単位変換係数。

```Julia
julia> angulartime(IAU,Metric) s⋅day⁻¹
86400.0
```
