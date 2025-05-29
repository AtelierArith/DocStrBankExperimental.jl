```julia
get_subcomponents(
    hybrid::PowerSystems.HybridSystem
) -> Channel{Any}

```

Return an iterator over the subcomponents in the HybridSystem.

# Examples

```julia
for subcomponent in get_subcomponents(hybrid_sys)
    @show subcomponent
end
subcomponents = collect(get_subcomponents(hybrid_sys))
```
