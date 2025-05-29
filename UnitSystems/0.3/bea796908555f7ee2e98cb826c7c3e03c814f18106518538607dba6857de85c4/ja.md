```Julia
statweber(U::UnitSystem) = magneticflux(𝟏,U,ESU)
```

静電単位の `magneticflux` (Wb)。

```Julia
julia> statweber(Metric) # Wb
299.792458

julia> statweber(EMU) # Mx
2.9979245800000004e10

julia> statweber(ESU) # statWb
1
```
