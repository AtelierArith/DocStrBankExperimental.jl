```Julia
phot(U::UnitSystem) = illuminance(𝟏,U,Gauss)
```

Historic unit of `illuminance` (lx).

```Julia
julia> phot(Metric) # lx
9999.999999999996

julia> phot(CGS) # ph
1

julia> phot(English) # fc
929.0303999999999
```
