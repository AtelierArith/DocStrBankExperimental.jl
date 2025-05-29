```
TimeSeries(t, v, x)
```

時間 t、変数 v、およびデータ x を持つ多変量時系列を構築します。

## 例

```@example 1
julia> t = 1:100;
julia> v = [:a, :b, :c];
julia> x = rand(100, 3);
julia> mts = TimeSeries(t, v, x)
julia> mts isa typeintersect(MultivariateTimeSeries, RegularTimeSeries)
```
