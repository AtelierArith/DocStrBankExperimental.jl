```
result_type(dist::PreMetric, Ta::Type, Tb::Type) -> T
result_type(dist::PreMetric, a::AbstractArray, b::AbstractArray) -> T
```

Infer the result type of metric `dist` with input type `Ta` and `Tb`, or input data `a` and `b`.
