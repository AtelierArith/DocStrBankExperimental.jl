```Julia
squaredegree(U::UnitSystem) = solidangle(𝟏,U,MetricDegree)
```

`solidangle`の単位は`degree`の二乗（rad²）です。

```Julia
julia> squaredegree(Engineering) # rad²
0.00030461741978670857

julia> squaredegree(MetricDegree) # deg²
1

julia> squaredegree(MetricArcminute) # amin²
3600.0

julia> squaredegree(MetricArcsecond) # asec²
1.296e7

julia> squaredegree(MetricGradian) # gon²
1.2345679012345678
```
