```Julia
astronomicalunit(U::UnitSystem) = length(𝟏,U,IAU)
```

国際天文学連合による標準天文単位（mまたはft）。

```Julia
julia> astronomicalunit(Metric) # m
1.495978707e11

julia> astronomicalunit(English) # ft
4.9080666240157477e11

julia> astronomicalunit(Metric)/lightspeed(Metric) # s
499.00478383615643
```
