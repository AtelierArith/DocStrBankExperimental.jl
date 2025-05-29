```
struct ValidationViolations <: QuEraSchema
```

Stores violations of hardware constraints from the user-supplied [`BloqadeExpr.RydbergHamiltonian`](@ref) as strings in sets. This is returned by [`validate`](@ref) and [`to_schema`](@ref).

# Fields

  * `lattice_violations::Set`: violations of hardware-supported lattice geometry
  * `misc_violations::Set`: violations that do not fall into other categories (e.g. number of shots)
  * `Δ_violations::Set`: violations of detuning waveform
  * `Ω_violations::Set`: violations of Rabi frequency waveform
  * `ϕ_violations::Set`: violations of Phase waveform
  * `δ_violations::Set`: violations of local detuning waveforms
