```Julia
radian(U::UnitSystem) = angle(𝟏,U,Metric)
```

Unit of `angle` which is dimensionless (rad).

```Julia
julia> radian(Engineering) # rad
1

julia> radian(MetricDegree) # deg
57.29577951308232

julia> radian(MetricArcminute) # amin
3437.7467707849396

julia> radian(MetricArcsecond) # asec
206264.80624709636

julia> radian(MetricGradian) # gon
63.66197723675813
```
