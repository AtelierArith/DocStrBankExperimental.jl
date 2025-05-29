```julia
iterate_supplemental_attributes(
    sys::PowerSystems.System
) -> Base.Iterators.Flatten{Base.Generator{Base.ValueIterator{Dict{DataType, Dict{Base.UUID, <:InfrastructureSystems.SupplementalAttribute}}}, InfrastructureSystems.var"#110#111"}}

```

Iterates over all supplemental_attributes.

# Examples

```julia
for supplemental_attribute in iterate_supplemental_attributes(sys)
    @show supplemental_attribute
end
```

See also: [`get_supplemental_attributes`](@ref)
