```
TimeSeries(t, x)
```

時間 `t` とデータ `x` を持つ単変量時系列を構築します。代わりに `TS(t, x)` を使用します。

## 例

```@example 1
julia> using TimeseriesTools, Unitful;
julia> t = 1:100
julia> x = rand(100)
julia> ts = TimeSeries(t, x)
julia> ts isa typeintersect(UnivariateTimeSeries, RegularTimeSeries)
```
