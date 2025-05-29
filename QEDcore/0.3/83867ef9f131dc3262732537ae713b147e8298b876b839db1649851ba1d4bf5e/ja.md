```
PhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    in_momenta::NTuple{N,AbstractFourMomentum},
    out_momenta::NTuple{M,AbstractFourMomentum},
)
```

与えられたプロセスに関して、入射粒子と出射粒子の与えられた運動量から位相空間点を構築します。
