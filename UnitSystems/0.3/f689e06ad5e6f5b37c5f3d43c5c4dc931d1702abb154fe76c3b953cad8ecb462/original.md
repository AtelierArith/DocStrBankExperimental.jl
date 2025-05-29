```Julia
henry(U::UnitSystem) = inductance(𝟏,U,Metric)
```

Metric unit of `inductance` (H).

```Julia
julia> henry(Metric) # H
1

julia> henry(EMU) # abH
9.999999999999999e8

julia> henry(ESU) # statH
1.112650056053618e-12
```
