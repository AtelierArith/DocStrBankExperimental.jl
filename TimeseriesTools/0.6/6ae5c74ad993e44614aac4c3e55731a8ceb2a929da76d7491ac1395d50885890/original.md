```
TimeSeries(t, x, timeunit::Unitful.Units)
```

Constructs a univariate time series with time `t`, data `x` and time units specified by `timeunit`. Note that you can add units to the elements of a time series `x` with, for example, `x*u"V"`.

## Examples

```@example 1
julia> using Unitful;
julia> t = 1:100;
julia> x = rand(100);
julia> ts = TimeSeries(t, x, u"ms")*u"V";
julia> ts isa Union{UnivariateTimeSeries, RegularTimeSeries, UnitfulTimeSeries}
```
