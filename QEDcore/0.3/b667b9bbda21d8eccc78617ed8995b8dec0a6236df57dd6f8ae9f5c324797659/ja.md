```
InPhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    in_momenta::NTuple{N,AbstractFourMomentum},
)
```

与えられた運動量から入力粒子のみを持つ[`PhaseSpacePoint`](@ref)を構築します。結果は`<: InPhaseSpacePoint`ですが、**<: OutPhaseSpacePoint**ではありません。
