```Julia
abfarad(U::UnitSystem) = capacitance(𝟏,U,EMU)
```

電磁単位の `capacitance` (F)。

```Julia
julia> abfarad(Metric) # F
1.0000000000000001e9

julia> abfarad(EMU) # abF
1

julia> abfarad(ESU) # statF
8.987551787368178e20
```
