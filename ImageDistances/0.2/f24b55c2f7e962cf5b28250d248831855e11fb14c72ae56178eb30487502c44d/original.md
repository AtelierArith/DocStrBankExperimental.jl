```
Cityblock <: Metric
SumAbsoluteDifference <: Metric
cityblock(x, y)
sad(x, y)
```

sum of absolute difference(sad), also known as [`Cityblock`](@ref) distance, is calculated by `sum(abs(x - y))`
