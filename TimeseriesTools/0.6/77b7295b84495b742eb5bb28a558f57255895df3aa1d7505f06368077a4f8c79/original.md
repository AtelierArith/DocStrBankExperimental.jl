```
TimeSeries(t, v, x)
```

Constructs a multivariate time series with time t, variable v, and data x.

## Examples

```@example 1
julia> t = 1:100;
julia> v = [:a, :b, :c];
julia> x = rand(100, 3);
julia> mts = TimeSeries(t, v, x)
julia> mts isa typeintersect(MultivariateTimeSeries, RegularTimeSeries)
```
