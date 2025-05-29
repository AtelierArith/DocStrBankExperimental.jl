```
DensityMatrixDiagonal(mode; component=0) <: AbstractHamiltonian
```

Represent a diagonal element of the single-particle density:

$$
\hat{n}_{i,σ} = \hat a^†_{i,σ} \hat a_{i,σ}
$$

where $i$ is the `mode` and $σ$ is the `component`. If `component` is zero, the sum over all components is computed.

# See also

  * [`single_particle_density`](@ref)
  * [`SingleParticleDensity`](@ref)
  * [`SingleParticleExcitation`](@ref)
