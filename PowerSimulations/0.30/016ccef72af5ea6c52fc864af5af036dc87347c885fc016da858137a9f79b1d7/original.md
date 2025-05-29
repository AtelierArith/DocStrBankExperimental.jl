```julia
template_unit_commitment(
;
    kwargs...
) -> PowerSimulations.ProblemTemplate

```

```
template_unit_commitment(; kwargs...)
```

Creates a `ProblemTemplate` with default DeviceModels for a Unit Commitment problem.

# Example

template = template*unit*commitment()

```

# Accepted Key Words
- `network::Type{<:PM.AbstractPowerModel}` : override default network model settings
- `devices::Vector{DeviceModel}` : override default `DeviceModel` settings
- `services::Vector{ServiceModel}` : override default `ServiceModel` settings
```
