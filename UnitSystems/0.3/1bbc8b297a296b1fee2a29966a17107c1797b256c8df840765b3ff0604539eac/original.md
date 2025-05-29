```Julia
farad(U::UnitSystem) = capacitance(𝟏,U,Metric)
```

Metric unit of `capacitance` (F).

```Julia
julia> farad(Metric) # F
1

julia> farad(EMU) # abF
1.0e-9

julia> farad(ESU) # statF
8.98755178736818e11
```
