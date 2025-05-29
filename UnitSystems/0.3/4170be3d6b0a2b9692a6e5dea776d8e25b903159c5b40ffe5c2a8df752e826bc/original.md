```Julia
lumen(U::UnitSystem) = luminousflux(𝟏,U,Metric)
```

Common unit of `luminousflux` (lm).

```Julia
julia> lumen(Metric) # lm
1

julia> lumen(CGS) # lm
1

julia> lumen(English) # lm
1
```
