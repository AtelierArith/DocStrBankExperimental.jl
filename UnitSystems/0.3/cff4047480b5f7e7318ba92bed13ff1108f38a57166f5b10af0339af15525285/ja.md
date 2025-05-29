```Julia
siderealmonth(U::UnitSystem) = gaussianmonth(U)/√(𝟏+lunarmass(IAU))
```

軌道 `time` は標準の `lunardistance` と地球-月系の `mass` (s) によって定義されます。

```Julia
julia> siderealmonth(Metric) # s
2.3573807233179593e6

julia> siderealmonth(MPH) # h
654.8279786994331

julia> siderealmonth(IAU) # D
27.28449911247638
```
