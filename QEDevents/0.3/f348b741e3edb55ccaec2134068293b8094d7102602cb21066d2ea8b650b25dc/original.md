```
SingleParticleDistribution
```

Base type for sample drawing from single particle distributions. The following interface functions should be implemented:

  * [`QEDevents._particle(d::SingleParticleDistribution)`](@ref): return associated particle
  * [`QEDevents._particle_direction(d::SingleParticleDistribution)`](@ref): return associated particle direction
  * [`QEDevents._randmom(d::SingleParticleDistribution)`](@ref): return momentum according to `d`
