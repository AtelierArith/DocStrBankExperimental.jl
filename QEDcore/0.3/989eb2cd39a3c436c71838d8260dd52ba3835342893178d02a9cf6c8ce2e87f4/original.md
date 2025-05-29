```
OutPhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    out_ps::Tuple{ParticleStateful},
)
```

Construct a [`PhaseSpacePoint`](@ref) with only output particles from [`ParticleStateful`](@ref)s. The result will be `<: OutPhaseSpacePoint` but **not** `<: InPhaseSpacePoint`.
