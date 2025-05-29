```Julia
statfarad(U::UnitSystem) = capacitance(𝟏,U,ESU)
```

静電単位の `capacitance` (F)。

```Julia
julia> statfarad(Metric) # F
1.1126500560536185e-12

julia> statfarad(EMU) # abF
1.1126500560536182e-21

julia> statfarad(ESU) # statF
1
```
