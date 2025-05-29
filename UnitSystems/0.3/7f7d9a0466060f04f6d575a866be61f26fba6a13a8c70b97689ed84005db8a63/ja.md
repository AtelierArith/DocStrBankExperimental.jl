```Julia
statmho(U::UnitSystem) = conductance(𝟏,U,ESU)
```

電気静電単位の `conductance` (S)。

```Julia
julia> statmho(Metric) # S
1.1126500560536185e-12

julia> statmho(EMU) # abS
1.1126500560536182e-21

julia> statmho(ESU) # statS
1
```
