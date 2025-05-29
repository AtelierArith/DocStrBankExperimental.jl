```
lwc_line(data::Vector{Tuple{TimeType,Real}}; kw...) -> LWCChart
lwc_line(data::Vector{Tuple{Real,Real}}; kw...) -> LWCChart
```

渡された `data` からタイムスタンプと値のベクトルを説明する [`LWCChart`](@ref) を作成します。
