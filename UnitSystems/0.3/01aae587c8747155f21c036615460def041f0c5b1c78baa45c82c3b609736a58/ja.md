```Julia
gaussianmonth(U::UnitSystem) = τ*sqrt(lunardistance(U)^3/earthmass(U)/gravitation(U))
```

軌道 `time` は、無視できる `mass` の衛星に対して `lunardistance` と `earthmass` によって定義されます (s)。

```Julia
julia> gaussianmonth(Metric) # s
2.3718343492584163e6

julia> gaussianmonth(MPH) # h
658.8428747940044

julia> gaussianmonth(IAU) # D
27.451786449750188
```
