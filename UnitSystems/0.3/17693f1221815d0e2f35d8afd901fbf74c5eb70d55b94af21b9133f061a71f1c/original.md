```Julia
turn(U::UnitSystem) = 2π/angle(U)
```

Complete rotation `angle` of revolution from a full circle.

```Julia
julia> turn(Engineering) # rad
6.283185307179586

julia> turn(MetricDegree) # deg
360.0

julia> turn(MetricArcminute) # amin
21600.0

julia> turn(MetricArcsecond) # asec
1.296e6

julia> turn(MetricGradian) # gon
400.0
```
