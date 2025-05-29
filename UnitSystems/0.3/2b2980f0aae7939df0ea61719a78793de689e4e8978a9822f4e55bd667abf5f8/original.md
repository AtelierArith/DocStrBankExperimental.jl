```Julia
footcandle(U::UnitSystem) = illuminance(𝟏,U,English)
```

English unit of `illuminance` (lx).

```Julia
julia> footcandle(Metric) # lx
10.76391041670972

julia> footcandle(CGS) # ph
0.0010763910416709721

julia> footcandle(English) # fc
1
```
