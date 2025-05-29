```julia
iterate_components(
    sys::PowerSystems.System
) -> InfrastructureSystems.FlattenIteratorWrapper{InfrastructureSystems.InfrastructureSystemsComponent, I} where I<:(Vector)

```

Iterates over all components.

# Examples

```julia
for component in iterate_components(sys)
    @show component
end
```

See also: [`get_components`](@ref)
