```julia
make_selector(
    component_type::Type{<:InfrastructureSystems.InfrastructureSystemsComponent},
    component_name::AbstractString;
    name
) -> InfrastructureSystems.NameComponentSelector

```

Make a [`ComponentSelector`](@ref) pointing to a single component with the given type and name. Optionally provide a name for the selector. Selectors constructed this way contain exactly one group, which contains one component if the target component exists and zero if it doesn't.

# Arguments

  * `component_type::Type{<:InfrastructureSystemsComponent}`: the type of the target component
  * `component_name::AbstractString`: the name of the target component
  * `name::Union{String, Nothing} = nothing`: the name of the selector; if not provided, one will be constructed automatically

# Examples

```julia
sel1 = make_selector(ThermalStandard, "322_CT_6")
sel2 = make_selector(ThermalStandard, "322_CT_6"; name = "my_selector")
```

See also: [`make_selector`](@ref) unified function documentation
