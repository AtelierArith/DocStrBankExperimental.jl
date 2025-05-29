```Julia
siderealmonth(U::UnitSystem) = gaussianmonth(U)/√(𝟏+lunarmass(IAU))
```

Orbit `time` defined by standard `lunardistance` and the Earth-Moon system `mass` (s).

```Julia
julia> siderealmonth(Metric) # s
2.3573807233179593e6

julia> siderealmonth(MPH) # h
654.8279786994331

julia> siderealmonth(IAU) # D
27.28449911247638
```
