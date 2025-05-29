```
OutPhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    out_ps::Tuple{ParticleStateful},
)
```

出力粒子のみを持つ[`PhaseSpacePoint`](@ref)を[`ParticleStateful`](@ref)から構築します。結果は`<: OutPhaseSpacePoint`ですが、**<: InPhaseSpacePoint**ではありません。
