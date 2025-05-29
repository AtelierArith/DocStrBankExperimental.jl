```julia
rebuild_selector(
    selector::InfrastructureSystems.ComponentSelector;
    name
) -> InfrastructureSystems.ListComponentSelector

```

Returns a [`ComponentSelector`](@ref) functionally identical to the input `selector` except with the changes to its fields specified in the keyword arguments.

# Examples

Suppose you have a selector with `name = "my_name`. If you instead wanted `name = "your_name`:

```julia
sel = make_selector(ThermalStandard, "322_CT_6"; name = "my_name")
sel_yours = rebuild_selector(sel; name = "your_name")
```
