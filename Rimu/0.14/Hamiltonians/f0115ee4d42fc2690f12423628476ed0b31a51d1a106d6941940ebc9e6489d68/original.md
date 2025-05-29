```
TwoParticleExcitation(i, j, k, l) <: AbstractOperator
```

Represent the ${ij, kl}$ element of the two-particle reduced density matrix:

$$
ρ̂^{(2)}_{ij, kl} =  â^†_{i} â^†_{j} â_{l} â_{k}
$$

where `i`, `j`, `k`, and `l` (all `<: Int`) specify the mode numbers.

# See also

  * [`single_particle_density`](@ref)
  * [`SingleParticleDensity`](@ref)
  * [`SingleParticleExcitation`](@ref)
