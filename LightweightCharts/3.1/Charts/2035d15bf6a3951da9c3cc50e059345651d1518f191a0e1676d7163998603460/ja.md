```
lwc_line(timestamps::Vector{TimeType}, values::Vector{Real}; kw...) -> LWCChart
lwc_line(timestamps::Vector{Real}, values::Vector{Real}; kw...) -> LWCChart
```

渡された `timestamps` と `values` から [`LWCChart`](@ref) を作成します。
