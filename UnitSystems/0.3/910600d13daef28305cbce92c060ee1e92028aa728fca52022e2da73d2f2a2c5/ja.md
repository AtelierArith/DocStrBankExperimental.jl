```Julia
day(U::UnitSystem) = 𝟐^3*𝟑*hour(U)
```

24 `hour` の間隔で定義された `time` の単位 (s)。

```Julia
julia> day(Metric) # s
86400

julia> day(MPH) # h
23.999999999999993

julia> day(IAU) # D
1.0
```
