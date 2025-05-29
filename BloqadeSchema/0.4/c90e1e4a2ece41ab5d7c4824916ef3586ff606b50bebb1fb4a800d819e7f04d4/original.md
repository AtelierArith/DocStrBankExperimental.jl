```
to_json_no_validation(lattice::Union{Vector,Lattice};
    ϕ::Maybe{PiecewiseConstantWaveform}=nothing,
    Ω::Maybe{PiecewiseLinearWaveform}=nothing,
    Δ::Maybe{PiecewiseLinearWaveform}=nothing,
    δ::Maybe{PiecewiseLinearWaveform}=nothing,
    Δi::Maybe{Vector{Number}}=nothing,kw...)
```

Converts `lattice`, `ϕ`, `Δ`, `δ`, and `Δi` to a JSON representation of a `QuEraTaskSpecification` instance WITHOUT ensuring the provided values are capable of being executed on the machine (fit within the  constraints of the device's capabilities)

See also [`to_json`](@ref)
