```
SimpleParticleContainer{PT<:AbstractParticle}() <: AbstractParticleContainer
```

Handles simulations with particles of one or more species with open and periodic boundaries. For performant time evolution the domain is partitioned into grid boxes with size `≥ interactionrange` where `InPartS.interactionrange` needs to be extended for new particle types and it has to be ensured that `interactionrange` is larger or equal to the maximum center-center distance between two interacting particles.
