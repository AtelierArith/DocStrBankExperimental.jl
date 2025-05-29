```
lwc_histogram(timestamps::Vector{TimeType}, values::Vector{Real}; kw...) -> LWCChart
lwc_histogram(timestamps::Vector{Real}, values::Vector{Real}; kw...) -> LWCChart
```

Creates a [`LWCChart`](@ref) from the passed `timestamps` and `values`.
