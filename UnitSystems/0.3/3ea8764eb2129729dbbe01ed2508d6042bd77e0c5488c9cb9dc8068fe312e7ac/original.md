```Julia
astronomicalunit(U::UnitSystem) = length(𝟏,U,IAU)
```

Standard astronomical unit from the International Astronomical Union (m or ft).

```Julia
julia> astronomicalunit(Metric) # m
1.495978707e11

julia> astronomicalunit(English) # ft
4.9080666240157477e11

julia> astronomicalunit(Metric)/lightspeed(Metric) # s
499.00478383615643
```
