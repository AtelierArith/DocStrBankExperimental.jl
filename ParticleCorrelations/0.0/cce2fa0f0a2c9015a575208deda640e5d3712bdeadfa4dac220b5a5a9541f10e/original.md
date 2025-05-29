```
pair_correlation(particles::Vector{AbstractParticle}, distances::AbstractVector)
```

Calculates the isotropic pair correlation from one configuration of particles. To use many configurations of particles, call this function for each, then take the average of the pair-correlation.
