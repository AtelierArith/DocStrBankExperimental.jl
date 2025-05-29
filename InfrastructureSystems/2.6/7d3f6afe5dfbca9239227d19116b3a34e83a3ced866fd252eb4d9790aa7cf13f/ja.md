```julia
iterate_windows(
    forecast::InfrastructureSystems.Scenarios
) -> Base.Generator{I, InfrastructureSystems.var"#105#106"{InfrastructureSystems.Scenarios}} where I<:(DataStructures.SDMKeyIteration{T} where T<:DataStructures.SortedDict)

```

予測のウィンドウを反復処理する

# 例

```julia
for window in iterate_windows(forecast)
    @show values(maximum(window))
end
```
