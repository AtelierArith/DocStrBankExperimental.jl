```
AccumulatedSeries{T}(::String = "")  (default T == Float64)
AccumulatedSeries{T}(::String = "", [::Int])  (default T == Float64)
```

A type of [`MonteCarloMeasurement`](@ref) that accumulates statistics for a  given observable while performing an *online* binning analysis provided by [`OnlineLogBinning.jl`](https://meese-wj.github.io/OnlineLogBinning.jl/stable/).

!!! note
    The *pre-allocated* [`AccumulatedSeries`](@ref) takes a `String` as the first argument and an `Int`eger denoting the anticipated datastream length as the second.

