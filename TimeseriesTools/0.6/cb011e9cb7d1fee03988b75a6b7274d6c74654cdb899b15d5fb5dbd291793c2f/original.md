```
times(x::AbstractTimeSeries)
```

Returns the time indices of the [`AbstractTimeSeries`](@ref) `x`.

## Examples

```@example 1
julia> t = 1:100;
julia> x = rand(100);
julia> ts = TimeSeries(t, x);
julia> times(ts) == t
```
