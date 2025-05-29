```julia
make_selector(
    content::InfrastructureSystems.ComponentSelector...;
    name
) -> InfrastructureSystems.ListComponentSelector

```

Make a [`ComponentSelector`](@ref) from several existing `ComponentSelector`s. Optionally provide a name for the selector. Selectors constructed this way contain one group for each of the selectors they were constructed with.

# Arguments

  * `content::ComponentSelector...`: the list of selectors that should form the groups
  * `name::Union{String, Nothing} = nothing`: the name of the selector; if not provided, one will be constructed automatically

# Examples

```julia
sel1 = make_selector(make_selector(ThermalStandard), make_selector(RenewableDispatch))
sel2 = make_selector(make_selector(ThermalStandard), make_selector(RenewableDispatch); name = "my_selector")
```

See also: [`make_selector`](@ref) unified function documentation
