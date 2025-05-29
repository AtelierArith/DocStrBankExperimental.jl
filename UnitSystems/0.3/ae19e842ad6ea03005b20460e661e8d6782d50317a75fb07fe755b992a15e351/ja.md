```Julia
coulomb(U::UnitSystem) = charge(𝟏,U,Metric)
```

メトリック単位の `charge` (C)。

```Julia
julia> coulomb(Metric) # C
1

julia> coulomb(EMU) # abC
0.1

julia> coulomb(ESU) # statC
2.9979245800000005e9
```
