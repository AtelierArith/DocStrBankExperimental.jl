```
SingleParticleExcitation(i, j) <: AbstractOperator
```

Represent the ${i,j}$ element of the single-particle reduced density matrix:

$$
ρ̂^{(1)}_{i,j} = â^†_{i} â_{j}
$$

where `i <: Int` and `j <: Int` specify the mode numbers.

# See also

  * [`single_particle_density`](@ref)
  * [`SingleParticleDensity`](@ref)
  * [`TwoParticleExcitation`](@ref)
