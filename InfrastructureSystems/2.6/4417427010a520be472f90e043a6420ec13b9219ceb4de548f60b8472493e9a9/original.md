```julia
get_name(
    selector::InfrastructureSystems.ComponentSelector
) -> Any

```

Get the name of the [`ComponentSelector`](@ref). This is either a user-specified name passed in at creation or a name automatically generated from the selector's specification.

# Examples

```julia
sel = make_selector(RenewableDispatch)
get_name(sel)  # "RenewableDispatch"
```
