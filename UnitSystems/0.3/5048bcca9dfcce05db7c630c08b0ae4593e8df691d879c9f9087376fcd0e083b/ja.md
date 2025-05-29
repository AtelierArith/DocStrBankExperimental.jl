```Julia
jovianyear(U::UnitSystem) = τ*day(U)*√(jupiterdistance(U)^3/solarmass(U)/gravitation(U))/√(𝟏+jupitermass(IAU))
```

軌道 `time` は `jupiterdistance` と太陽-木星系の `mass` によって定義されます (s)。

```Julia
julia> jovianyear(Metric) # s
3.235198684088133e13

julia> jovianyear(MPH) # h
2.4962952809322e6

julia> jovianyear(IAU) # D
4333.845973840625
```
