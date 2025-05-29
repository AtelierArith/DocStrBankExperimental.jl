```julia
from_json(
    io::Union{IO, String},
    _::Type{T<:InfrastructureSystems.InfrastructureSystemsType}
) -> PowerSystems.System

```

Deserializes a InfrastructureSystemsType from String or IO.
