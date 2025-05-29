```Julia
arcsecond(U::UnitSystem) = angle(𝟏,U,MetricArcsecond)
```

`angle`の単位で、`arcminute`を`60`の部分に分割します（ラジアン）。

```Julia
julia> arcsecond(Engineering) # rad
4.84813681109536e-6

julia> arcsecond(MetricDegree) # deg
0.0002777777777777778

julia> arcsecond(MetricArcminute) # amin
0.01666666666666667

julia> arcsecond(MetricArcsecond) # asec
1

julia> arcsecond(MetricGradian) # gon
0.00030864197530864197
```
