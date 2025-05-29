```
times(x::AbstractTimeSeries)
```

[`AbstractTimeSeries`](@ref) `x` の時間インデックスを返します。

## 例

```@example 1
julia> t = 1:100;
julia> x = rand(100);
julia> ts = TimeSeries(t, x);
julia> times(ts) == t
```
