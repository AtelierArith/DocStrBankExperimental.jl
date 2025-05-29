```
name(meas::MonteCarloMeasurement)
```

Return the `name` defined by the input [`MonteCarloMeasurement`](@ref).

```jldoctest
julia> meas = TimeSeries("Walter White");

julia> name(meas)
"Walter White"
```
