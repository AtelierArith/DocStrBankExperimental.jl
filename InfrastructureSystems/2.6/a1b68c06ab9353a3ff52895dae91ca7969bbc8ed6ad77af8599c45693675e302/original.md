```julia
iterate_windows(
    forecast::InfrastructureSystems.DeterministicSingleTimeSeries
) -> Union{Tuple{Any}, Base.Generator{I, InfrastructureSystems.var"#146#147"{InfrastructureSystems.DeterministicSingleTimeSeries}} where I<:(StepRangeLen{T, R, S, Int64} where {T, R>:Dates.DateTime, S})}

```

Iterate over the windows in a forecast

# Examples

```julia
for window in iterate_windows(forecast)
    @show values(maximum(window))
end
```
