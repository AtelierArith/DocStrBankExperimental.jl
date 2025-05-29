```Julia
gradian(U::UnitSystem) = angle(𝟏,U,MetricGradian)
```

`angle`の単位は`turn`を`400`の部分に分割します（ラジアン）。

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
