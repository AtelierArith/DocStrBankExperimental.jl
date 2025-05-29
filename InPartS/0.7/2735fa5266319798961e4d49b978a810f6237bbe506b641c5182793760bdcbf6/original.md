```
ParticlesObstacleContainer{PT <: AbstractParticle, SO}() <: AbstractParticleContainer
```

Handler suitable for simulations that contain both particles and obstacles such as walls. The logic for particles is identical to that of the `SimpleParticleContainer`. Objects passed as obstacles are static. They cannot move but may have arbitrary size. To allow for efficient time evolution obstacles have to implement `InPartS.interactionpolygon` that allows precomputation of the gridboxes relevant for interactions.
