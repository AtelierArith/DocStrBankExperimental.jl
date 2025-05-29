```Julia
year(U::UnitSystem) = aⱼ*day(U)
```

Unit of `time` defined by Julian calendar year interval (s).

```Julia
julia> year(Metric) # s
3.15576e7

julia> year(MPH) # h
8765.999999999998

julia> year(IAU) # D
365.25
```
