```
name(meas::MonteCarloMeasurement)
```

入力によって定義された`name`を返します[`MonteCarloMeasurement`](@ref)。

```jldoctest
julia> meas = TimeSeries("Walter White");

julia> name(meas)
"Walter White"
```
