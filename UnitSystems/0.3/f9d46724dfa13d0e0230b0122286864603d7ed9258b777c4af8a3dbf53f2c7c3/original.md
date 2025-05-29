```Julia
siemens(U::UnitSystem) = conductance(𝟏,U,Metric)
```

Metric unit of `conductance` (S).

```Julia
julia> siemens(Metric) # S
1

julia> siemens(EMU) # abS
1.0e-9

julia> siemens(ESU) # statS
8.98755178736818e11
```
