```Julia
synodicmonth(U::UnitSystem) = 𝟏/(𝟏/siderealmonth(U)-𝟏/siderealyear(U))
```

軌道 `time` は、太陽-地球-月系の `siderealmonth` と `siderealyear` によって定義されます (s)。

```Julia
julia> synodicmonth(Metric) # s
2.5476922935413797e6

julia> synodicmonth(MPH) # h
707.6923037614943

julia> synodicmonth(IAU) # D
29.48717932339559
```
