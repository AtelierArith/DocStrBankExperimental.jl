```Julia
year(U::UnitSystem) = aⱼ*day(U)
```

ユリウス暦年の間隔で定義された `time` の単位 (s)。

```Julia
julia> year(Metric) # s
3.15576e7

julia> year(MPH) # h
8765.999999999998

julia> year(IAU) # D
365.25
```
