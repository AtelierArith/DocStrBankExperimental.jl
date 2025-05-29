```Julia
spat(U::UnitSystem) = 4π/solidangle(U)
```

完全な球から点の周りの球面 `solidangle` を完成させます。

```Julia
julia> spat(Engineering) # rad²
12.566370614359172

julia> spat(MetricDegree) # deg²
41252.96124941927

julia> spat(MetricArcminute) # amin²
1.485106604979094e8

julia> spat(MetricArcsecond) # asec²
5.3463837779247375e11

julia> spat(MetricGradian) # gon²
50929.581789406504
```
