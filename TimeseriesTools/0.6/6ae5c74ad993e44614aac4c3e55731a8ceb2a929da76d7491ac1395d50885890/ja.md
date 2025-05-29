```
TimeSeries(t, x, timeunit::Unitful.Units)
```

時間 `t`、データ `x`、および `timeunit` で指定された時間単位を持つ単変量時系列を構築します。時系列 `x` の要素に単位を追加することができ、例えば `x*u"V"` のように使用できます。

## 例

```@example 1
julia> using Unitful;
julia> t = 1:100;
julia> x = rand(100);
julia> ts = TimeSeries(t, x, u"ms")*u"V";
julia> ts isa Union{UnivariateTimeSeries, RegularTimeSeries, UnitfulTimeSeries}
```
