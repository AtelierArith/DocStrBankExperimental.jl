```Julia
gradian(U::UnitSystem) = angle(𝟏,U,MetricGradian)
```

Unit of `angle` which divides a `turn` into `400` parts (rad).

```Julia
julia> gradian(Engineering) # rad
0.015707963267948967

julia> gradian(MetricDegree) # deg
0.8999999999999999

julia> gradian(MetricArcminute) # amin
54.0

julia> gradian(MetricArcsecond) # asec
3240.0

julia> gradian(MetricGradian) # gon
1
```
