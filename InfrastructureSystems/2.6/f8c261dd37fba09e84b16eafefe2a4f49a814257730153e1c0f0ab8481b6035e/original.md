```julia
serialize(
    val::InfrastructureSystems.InfrastructureSystemsType
) -> Vector{Dict{String, Any}}

```

Serialize the Julia value into standard types that can be converted to non-Julia formats, such as JSON. In cases where val is an instance of a struct, return a Dict. In cases where val is a scalar value, return that value.
