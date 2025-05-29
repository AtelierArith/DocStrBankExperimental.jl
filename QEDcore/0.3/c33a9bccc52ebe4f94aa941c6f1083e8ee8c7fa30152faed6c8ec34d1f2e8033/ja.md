```
OutPhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    out_momenta::NTuple{N,AbstractFourMomentum},
)
```

与えられた運動量から出力粒子のみを持つ[`PhaseSpacePoint`](@ref)を構築します。結果は`<: OutPhaseSpacePoint`ですが、**<: InPhaseSpacePoint**ではありません。
