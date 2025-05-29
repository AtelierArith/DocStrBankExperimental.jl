```
InPhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    in_ps::Tuple{ParticleStateful},
)

[`PhaseSpacePoint`](@ref)を[`ParticleStateful`](@ref)からの入力粒子のみで構築します。結果は`<: InPhaseSpacePoint`ですが、**<: OutPhaseSpacePoint**ではありません。
```
