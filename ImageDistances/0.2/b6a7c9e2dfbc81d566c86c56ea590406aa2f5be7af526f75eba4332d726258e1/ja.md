```
SqEuclidean <: Metric
SumSquaredDifference <: Metric
sqeuclidean(x, y)
ssd(x, y)
```

二乗和の差（ssd）は、[`SqEuclidean`](@ref) 距離としても知られ、`sum(abs2(x - y))` によって計算されます。
