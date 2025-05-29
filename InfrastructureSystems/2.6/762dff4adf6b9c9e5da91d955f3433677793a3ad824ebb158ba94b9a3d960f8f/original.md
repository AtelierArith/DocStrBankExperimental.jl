```julia
rebuild_selector(
    selector::InfrastructureSystems.ListComponentSelector;
    name,
    groupby
) -> InfrastructureSystems.ListComponentSelector

```

Returns a [`ComponentSelector`](@ref) functionally identical to the input `selector` except with the changes to its fields specified in the keyword arguments. It is not guaranteed that the result will have the same concrete type.

# Examples

Suppose you have a selector with manual groups and you want to group by `:each`:

```julia
sel = make_selector(make_selector(ThermalStandard), make_selector(RenewableDispatch))
sel_each = rebuild_selector(sel; groupby = :each)  # will be a RegroupedComponentSelector
```
