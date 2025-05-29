```Julia
arcminute(U::UnitSystem) = angle(𝟏,U,MetricArcminute)
```

Unit of `angle` which divides a `degree` into `60` parts (rad).

```Julia
julia> arcminute(Engineering) # rad
0.0002908882086657216

julia> arcminute(MetricDegree) # deg
0.016666666666666663

julia> arcminute(MetricArcminute) # amin
1

julia> arcminute(MetricArcsecond) # asec
60.0

julia> arcminute(MetricGradian) # gon
0.018518518518518517
```
