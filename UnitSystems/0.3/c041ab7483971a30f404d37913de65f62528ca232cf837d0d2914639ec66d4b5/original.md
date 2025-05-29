```Julia
steradian(U::UnitSystem) = solidangle(𝟏,U,Metric)
```

Unit of `solidangle` which is dimensionless (rad²).

```Julia
julia> steradian(Engineering) # rad²
1

julia> steradian(MetricDegree) # deg²
3282.806350011744

julia> steradian(MetricArcminute) # amin²
1.181810286004228e7

julia> steradian(MetricArcsecond) # asec²
4.25451702961522e10

julia> steradian(MetricGradian) # gon²
4052.8473456935108
```
