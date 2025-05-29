```
lwc_baseline(data::Vector{Tuple{TimeType,Real}}; kw...) -> LWCChart
lwc_baseline(data::Vector{Tuple{Real,Real}}; kw...) -> LWCChart
```

Creates a [`LWCChart`](@ref) from the passed `data` that describes a vector of timestamps and values.
