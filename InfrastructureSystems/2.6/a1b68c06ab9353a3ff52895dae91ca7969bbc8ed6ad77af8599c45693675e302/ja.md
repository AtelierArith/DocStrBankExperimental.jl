```julia
iterate_windows(
    forecast::InfrastructureSystems.DeterministicSingleTimeSeries
) -> Union{Tuple{Any}, Base.Generator{I, InfrastructureSystems.var"#146#147"{InfrastructureSystems.DeterministicSingleTimeSeries}} where I<:(StepRangeLen{T, R, S, Int64} where {T, R>:Dates.DateTime, S})}

```

予測のウィンドウを反復処理します

# 例

```julia
for window in iterate_windows(forecast)
    @show values(maximum(window))
end
```
