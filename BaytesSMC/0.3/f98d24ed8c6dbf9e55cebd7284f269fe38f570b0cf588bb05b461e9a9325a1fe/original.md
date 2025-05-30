```julia
struct SMC{A<:BaytesSMC.SMCParticles, B<:BaytesSMC.SMCTune} <: BaytesCore.AbstractAlgorithm
```

SMC Algorithm.

# Fields

  * `particles::BaytesSMC.SMCParticles`
  * `tune::BaytesSMC.SMCTune`
