```julia
Constant(
    _::Type{Measurements.Measurement},
    units::Vector{Unitful.FreeUnits{N, D, nothing} where {N, D}}
) -> PhysicalParticles.Constant

```

Construct an immutable struct storing basic physical constants in `Measurement` corresponding to `units` (default is `uAstro`).
