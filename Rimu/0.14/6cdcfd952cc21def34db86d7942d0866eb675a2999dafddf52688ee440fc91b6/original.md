```
SingleParticleDensity(; save_every=1, component) <: PostStepStrategy
```

[`PostStepStrategy`](@ref)  to  compute the diagonal [`single_particle_density`](@ref). It records a `Tuple` with the same `eltype` as the vector.

Computing the density at every time step can be expensive. This cost can be reduced by setting the `save_every` argument to a higher value. If the value is set, a vector of zeros is recorded when the saving is skipped.

If the address type has multiple components, the `component` argument can be used to compute the density on a per-component basis.

The density is not normalized, and must be divided by the vector `norm(⋅,2)` squared.

# See also

  * [`single_particle_density`](@ref)
  * [`DensityMatrixDiagonal`](@ref)
