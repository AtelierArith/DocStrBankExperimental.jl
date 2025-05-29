```
InPhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    in_ps::Tuple{ParticleStateful},
)

Construct a [`PhaseSpacePoint`](@ref) with only input particles from [`ParticleStateful`](@ref)s. The result will be `<: InPhaseSpacePoint` but **not** `<: OutPhaseSpacePoint`.
```
