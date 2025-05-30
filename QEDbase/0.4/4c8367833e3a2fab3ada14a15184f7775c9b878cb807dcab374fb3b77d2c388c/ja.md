```
momentum(psp::AbstractPhaseSpacePoint, dir::ParticleDirection, species::AbstractParticleType)
```

与えられた [`AbstractPhaseSpacePoint`](@ref) における粒子の運動量を `dir` と `species` で返します。粒子が1つだけの場合に限ります。複数または存在しない場合は、[`InvalidInputError`](@ref) がスローされます。
