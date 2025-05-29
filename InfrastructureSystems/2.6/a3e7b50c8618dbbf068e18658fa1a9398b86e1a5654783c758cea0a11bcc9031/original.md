```julia
make_selector(
    component_type::Type{<:InfrastructureSystems.InfrastructureSystemsComponent};
    groupby,
    name
) -> InfrastructureSystems.TypeComponentSelector

```

Make a [`ComponentSelector`](@ref) from a type of component. Optionally provide a grouping behavior and/or name for the selector. Selectors constructed this way point to all the components of the given type, grouped by the `groupby` argument (see the base [`make_selector`](@ref) documentation).

# Arguments

  * `component_type::Type{<:InfrastructureSystemsComponent}`: the type of component to select
  * `groupby::Union{Symbol, Function} = :each`: the grouping behavior (see the base [`make_selector`](@ref) documentation)
  * `name::Union{String, Nothing} = nothing`: the name of the selector; if not provided, one will be constructed automatically

# Examples

```julia
sel1 = make_selector(RenewableDispatch)
sel2 = make_selector(RenewableDispatch; groupby = :all)
sel3 = make_selector(RenewableDispatch; name = "my_selector")
```

See also: [`make_selector`](@ref) unified function documentation
