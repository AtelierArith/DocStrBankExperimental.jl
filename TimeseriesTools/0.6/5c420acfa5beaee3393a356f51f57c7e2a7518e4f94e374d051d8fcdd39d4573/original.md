```
TimeSeries(t, x)
```

Constructs a univariate time series with time `t` and data `x`. Alteratively, use `TS(t, x)`

## Examples

```@example 1
julia> using TimeseriesTools, Unitful;
julia> t = 1:100
julia> x = rand(100)
julia> ts = TimeSeries(t, x)
julia> ts isa typeintersect(UnivariateTimeSeries, RegularTimeSeries)
```
