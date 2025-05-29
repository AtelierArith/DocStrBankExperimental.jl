```Julia
stattesla(U::UnitSystem) = magneticfluxdensity(𝟏,U,ESU)
```

Electrostatic unit of `magneticfluxdensity` (T).

```Julia
julia> stattesla(Metric) # T
2.997924579999999e6

julia> stattesla(EMU) # G
2.9979245800000004e10

julia> stattesla(ESU) # statT
1
```
