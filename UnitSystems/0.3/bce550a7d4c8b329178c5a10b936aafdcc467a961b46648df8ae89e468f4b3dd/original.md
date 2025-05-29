```Julia
weber(U::UnitSystem) = magneticflux(𝟏,U,Metric)
```

Metric unit of `magneticflux` (Wb).

```Julia
julia> weber(Metric) # Wb
1

julia> weber(EMU) # Mx
1.0e8

julia> weber(ESU) # statWb
0.0033356409519815196
```
