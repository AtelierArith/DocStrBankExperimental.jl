```Julia
lux(U::UnitSystem) = illuminance(𝟏,U,Metric)
```

Metric unit of `illuminance` (lx).

```Julia
julia> lux(Metric) # lx
1

julia> lux(CGS) # ph
0.00010000000000000003

julia> lux(English) # fc
0.09290304
```
