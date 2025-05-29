```
DensityDiffusion
```

An abstract supertype of all density diffusion formulations.

Currently, the following formulations are available:

| Formulation                                 | Suitable for Steady-State Simulations | Low Computational Cost |
|:------------------------------------------- |:------------------------------------- |:---------------------- |
| [`DensityDiffusionMolteniColagrossi`](@ref) | ❌                                     | ✅                      |
| [`DensityDiffusionFerrari`](@ref)           | ❌                                     | ✅                      |
| [`DensityDiffusionAntuono`](@ref)           | ✅                                     | ❌                      |

See [Density Diffusion](@ref density_diffusion) for a comparison and more details.
