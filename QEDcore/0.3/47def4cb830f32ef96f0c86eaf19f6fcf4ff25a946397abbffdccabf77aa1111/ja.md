```
ParticleStateful{DIR, SPECIES}(mom::AbstractFourMomentum)
ParticleStateful{DIR, SPECIES, EL}(mom::EL)
```

与えられた運動量から、完全にまたは部分的に指定された型の[`ParticleStateful`](@ref)を構築します。
