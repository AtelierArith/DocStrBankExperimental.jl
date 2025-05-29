```Julia
phot(U::UnitSystem) = illuminance(𝟏,U,Gauss)
```

歴史的な `illuminance` (lx) の単位。

```Julia
julia> phot(Metric) # lx
9999.999999999996

julia> phot(CGS) # ph
1

julia> phot(English) # fc
929.0303999999999
```
