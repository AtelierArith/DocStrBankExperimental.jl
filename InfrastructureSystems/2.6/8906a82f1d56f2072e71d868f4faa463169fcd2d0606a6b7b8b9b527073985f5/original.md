```julia
rebuild_selector(
    selector::InfrastructureSystems.DynamicallyGroupedComponentSelector;
    name,
    groupby
) -> Any

```

Returns a [`ComponentSelector`](@ref) functionally identical to the input `selector` except with the changes to its fields specified in the keyword arguments.

# Examples

Suppose you have a selector with `groupby = :all`. If you instead wanted `groupby = :each`:

```julia
sel = make_selector(ThermalStandard; groupby = :all)
sel_each = rebuild_selector(sel; groupby = :each)
```
