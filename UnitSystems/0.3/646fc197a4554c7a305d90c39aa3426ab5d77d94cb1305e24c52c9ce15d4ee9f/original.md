```Julia
boiling(U::UnitSystem) = temperature(T₀+Constant(99.9839),U)
```

Standard `temperature` reference at `boiling` point of water (K or °R).

```Julia
julia> boiling(Metric) # K
373.1339

julia> boiling(SI2019) # K
373.13389987173747

julia> boiling(English) # °R
671.6410199999999
```
