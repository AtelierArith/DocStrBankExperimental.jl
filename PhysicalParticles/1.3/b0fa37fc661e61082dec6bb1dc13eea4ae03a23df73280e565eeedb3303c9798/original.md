```julia
Constant(
    _::Type{BigFloat},
    units::Vector{Unitful.FreeUnits{N, D, nothing} where {N, D}}
) -> PhysicalParticles.Constant

```

Construct an immutable struct storing basic physical constants in `BigFloat` corresponding to `units` (default is `uAstro`).
