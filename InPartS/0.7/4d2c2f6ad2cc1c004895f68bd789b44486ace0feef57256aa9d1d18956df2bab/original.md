```
POLOContainer{N, PT <: AbstractParticle, SO, LO}() <: AbstractParticleContainer
```

A more flexible handler that can work with simulations containing (microscopic) particles, obstacles and mesoscopic objects. This can be useful when some dynamic objects are significantly larger than most particles and thus should not limit the performance sensitive grid box sizes.

Currently no optimization for these large objects is implemented. The interaction function is computed for every particle - large object pair.

!!! warn
    Despite the fact that it already has a dimensionality parameters, the POLOContainer currently only works for 2D simulations. You will find it quite impossible to actually construct a POLOContainer with N ≠ 2.

