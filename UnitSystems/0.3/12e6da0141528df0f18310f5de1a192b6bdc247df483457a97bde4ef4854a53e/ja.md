```Julia
gaussianyear(U::UnitSystem) = turn(U)/gaussgravitation(U)
```

軌道 `time` は、無視できる `mass` の衛星に対する `gaussgravitation` 定数 `kG` によって定義されます (s)。

```Julia
julia> gaussianyear(Metric) # s
3.1558195988402087e7

julia> gaussianyear(MPH) # h
8766.16555233391

julia> gaussianyear(IAU) # D
365.25689801391303
```
