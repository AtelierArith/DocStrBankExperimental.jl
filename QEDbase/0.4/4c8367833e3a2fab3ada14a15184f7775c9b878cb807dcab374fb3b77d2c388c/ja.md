```
momentum(psp::AbstractPhaseSpacePoint, dir::ParticleDirection, species::AbstractParticleType)
```

与えられた [`AbstractPhaseSpacePoint`](@ref) における粒子の運動量を `dir` と `species` で返します。ただし、該当する粒子が1つだけ存在する場合に限ります。複数存在するか、存在しない場合は、[`InvalidInputError`](@ref) がスローされます。
