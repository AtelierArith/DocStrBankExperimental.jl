```
lwc_candlestick(data::Vector{Tuple{D,O,H,L,C}}; kw...) -> LWCChart
```

渡された `data` からキャンドルのベクトルを説明する [`LWCChart`](@ref) を作成します。ここで、`D` は `Real` または `TimeType` で、`O,H,L,C` は `Real` です。
