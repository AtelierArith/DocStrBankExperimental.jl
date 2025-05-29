```julia
from_json(
    io::Union{IO, String},
    _::Type{T<:InfrastructureSystems.InfrastructureSystemsType}
) -> PowerSystems.System

```

StringまたはIOからInfrastructureSystemsTypeをデシリアライズします。
