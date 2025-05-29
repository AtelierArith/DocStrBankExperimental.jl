```Julia
abcoulomb(U::UnitSystem) = charge(𝟏,U,EMU)
```

電磁単位の `charge` (C)。

```Julia
julia> abcoulomb(Metric) # C
10.0

julia> abcoulomb(EMU) # abC
1

julia> abcoulomb(ESU) # statC
2.9979245800000004e10
```
