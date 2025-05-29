```Julia
lumen(U::UnitSystem) = luminousflux(𝟏,U,Metric)
```

`luminousflux` の一般的な単位 (lm)。

```Julia
julia> lumen(Metric) # lm
1

julia> lumen(CGS) # lm
1

julia> lumen(English) # lm
1
```
