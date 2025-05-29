```Julia
hour(U::UnitSystem) = 𝟐^2*𝟑*𝟓*minute(U)
```

Unit of `time` defined by 60 `minute` intervals (s).

```Julia
julia> hour(Metric) # s
3600

julia> hour(MPH) # h
0.9999999999999998

julia> hour(IAU) # D
0.041666666666666664
```
