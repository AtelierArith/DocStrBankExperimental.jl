```Julia
degree(U::UnitSystem) = angle(𝟏,U,MetricDegree)
```

`angle`の単位で、`turn`を`360`の部分に分割します（rad）。

```Julia
julia> degree(Engineering) # rad
0.017453292519943295

julia> degree(MetricDegree) # deg
1

julia> degree(MetricArcminute) # amin
60.0

julia> degree(MetricArcsecond) # asec
3600.0

julia> degree(MetricGradian) # gon
1.1111111111111112
```
