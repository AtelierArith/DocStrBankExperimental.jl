```
TimeSeries{T <: Number} <: MonteCarloMeasurement
```

[`MonteCarloMeasurement`](@ref) の一種で、`datastream::Vector{T}` に測定値を格納します。統計は*オンライン*方式で蓄積されません。
