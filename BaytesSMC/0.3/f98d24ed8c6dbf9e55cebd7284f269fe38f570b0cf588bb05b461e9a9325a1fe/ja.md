```julia
struct SMC{A<:BaytesSMC.SMCParticles, B<:BaytesSMC.SMCTune} <: BaytesCore.AbstractAlgorithm
```

SMCアルゴリズム。

# フィールド

  * `particles::BaytesSMC.SMCParticles`
  * `tune::BaytesSMC.SMCTune`
