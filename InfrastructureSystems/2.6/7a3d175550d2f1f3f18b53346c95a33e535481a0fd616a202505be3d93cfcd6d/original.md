```julia
make_selector(
    component::InfrastructureSystems.InfrastructureSystemsComponent;
    name
) -> InfrastructureSystems.NameComponentSelector

```

Make a [`ComponentSelector`](@ref) from a component, pointing to a single component with the same type and name as the one given. Optionally provide a name for the selector. Selectors constructed this way contain exactly one group, which contains one component if the target component exists and zero if it doesn't.

# Arguments

  * `component::InfrastructureSystemsComponent`: the component whose type and name specify the target of this selector
  * `name::Union{String, Nothing} = nothing`: the name of the selector; if not provided, one will be constructed automatically

# Examples

```julia
sel1 = make_selector(my_component)
sel2 = make_selector(my_component; name = "my_selector")
```

See also: [`make_selector`](@ref) unified function documentation
