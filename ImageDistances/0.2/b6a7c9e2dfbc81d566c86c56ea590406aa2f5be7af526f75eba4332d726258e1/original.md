```
SqEuclidean <: Metric
SumSquaredDifference <: Metric
sqeuclidean(x, y)
ssd(x, y)
```

sum of squared difference(ssd), also known as [`SqEuclidean`](@ref) distance, is calculated by `sum(abs2(x - y))`
