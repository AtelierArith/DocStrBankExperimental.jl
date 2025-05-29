```julia
template_economic_dispatch(
;
    kwargs...
) -> PowerSimulations.ProblemTemplate

```

```
template_economic_dispatch(; kwargs...)
```

Creates a `ProblemTemplate` with default DeviceModels for an Economic Dispatch problem.

# Example

template = template*economic*dispatch()

```

# Accepted Key Words
- `network::Type{<:PM.AbstractPowerModel}` : override default network model settings
- `devices::Vector{DeviceModel}` : override default `DeviceModel` settings
- `services::Vector{ServiceModel}` : override default `ServiceModel` settings
```
