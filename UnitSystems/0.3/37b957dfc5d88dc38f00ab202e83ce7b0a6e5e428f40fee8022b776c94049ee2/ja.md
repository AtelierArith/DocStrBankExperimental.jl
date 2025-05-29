```Julia
spatian(U::UnitSystem) = angle(𝟏,U,MetricSpatian)
```

次元のない `angle` の単位（rad）。

```Julia
julia> spatian(Engineering) # rad
3.544907701811032

julia> spatian(MetricDegree) # deg
203.10825007719225

julia> spatian(MetricArcminute) # amin
12186.495004631537

julia> spatian(MetricArcsecond) # asec
731189.7002778922

julia> spatian(MetricGradian) # gon
225.6758334191025
```
