```
to_schema_no_validation(lattice::Union{Vector,Lattice};
    ϕ::Maybe{PiecewiseConstantWaveform}=nothing,
    Ω::Maybe{PiecewiseLinearWaveform}=nothing,
    Δ::Maybe{PiecewiseLinearWaveform}=nothing,
    δ::Maybe{PiecewiseLinearWaveform}=nothing,
    Δi::Maybe{Vector{Number}}=nothing, 
    nshots::Int,
    device_capabilities::DeviceCapabilities=get_device_capabilities())
to_schema_no_validation(lattice::Union{Vector,Lattice},
    ϕ::Maybe{PiecewiseConstantWaveform},
    Ω::Maybe{PiecewiseLinearWaveform},
    Δ::Maybe{PiecewiseLinearWaveform},
    δ::Maybe{PiecewiseLinearWaveform},
    Δi::Maybe{Vector{Number}}, 
    params::SchemaTranslationParams)
```

Converts `lattice`, `ϕ`, `Δ`, `δ`, and `Δi` to a `QuEraTaskSpecification` instance WITHOUT ensuring the provided values are capable of being executed on the machine (fit within the  constraints of the device's capabilities).

If `params` is not already provided, it is constructed automatically from `nshots::Int` and `device_capabilities`.

See also [`to_schema`](@ref)
