```julia
iterate_windows(
    forecast::InfrastructureSystems.Deterministic
) -> Base.Generator{I, InfrastructureSystems.var"#105#106"{InfrastructureSystems.Deterministic}} where I<:(DataStructures.SDMKeyIteration{T} where T<:DataStructures.SortedDict)

```

予測のウィンドウを反復処理します

# 例

```julia
for window in iterate_windows(forecast)
    @show values(maximum(window))
end
```
