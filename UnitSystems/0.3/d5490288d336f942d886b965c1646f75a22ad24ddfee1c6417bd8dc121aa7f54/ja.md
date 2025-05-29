```Julia
tesla(U::UnitSystem) = magneticfluxdensity(𝟏,U,Metric)
```

`magneticfluxdensity`のメトリック単位 (T)。

```Julia
julia> tesla(Metric) # T
1

julia> tesla(EMU) # G
10000.000000000005

julia> tesla(ESU) # statT
3.3356409519815214e-7
```
