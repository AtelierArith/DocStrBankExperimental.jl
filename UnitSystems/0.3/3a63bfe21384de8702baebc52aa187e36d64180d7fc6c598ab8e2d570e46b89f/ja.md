```Julia
stathenry(U::UnitSystem) = inductance(𝟏,U,ESU)
```

静電単位の `inductance` (H)。

```Julia
julia> stathenry(Metric) # H
8.987551787368176e11

julia> stathenry(EMU) # abH
8.987551787368178e20

julia> stathenry(ESU) # statH
1
```
