```
lwc_candlestick(data::Vector{Tuple{D,O,H,L,C}}; kw...) -> LWCChart
```

Creates a [`LWCChart`](@ref) from the passed `data` that describes a vector of candles. Here `D` is a `Real` or `TimeType` and `O,H,L,C` are `Real`s.
