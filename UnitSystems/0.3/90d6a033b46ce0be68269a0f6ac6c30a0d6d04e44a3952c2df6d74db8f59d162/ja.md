```Julia
minute(U::UnitSystem) = 𝟐^2*𝟑*𝟓*second(U)
```

60 `second` の間隔によって定義される `time` の単位 (s)。

```Julia
julia> minute(Metric) # s
60

julia> minute(MPH) # h
0.016666666666666663

julia> minute(IAU) # D
0.0006944444444444444
```
