```julia
iterate_windows(
    forecast::InfrastructureSystems.Deterministic
) -> Base.Generator{I, InfrastructureSystems.var"#105#106"{InfrastructureSystems.Deterministic}} where I<:(DataStructures.SDMKeyIteration{T} where T<:DataStructures.SortedDict)

```

Iterate over the windows in a forecast

# Examples

```julia
for window in iterate_windows(forecast)
    @show values(maximum(window))
end
```
