```Julia
hour(U::UnitSystem) = 𝟐^2*𝟑*𝟓*minute(U)
```

60 `minute` インターバルによって定義される `time` の単位 (s)。

```Julia
julia> hour(Metric) # s
3600

julia> hour(MPH) # h
0.9999999999999998

julia> hour(IAU) # D
0.041666666666666664
```
