```julia
struct InitialTrajectory{K<:BaytesFilters.ParticleKernel, C<:BaytesFilters.ParticleReferencing, M<:BaytesFilters.ParticleFilterMemory}
```

Contains information to obtain reference trajectory for sampling process.

# Fields

  * `kernel::BaytesFilters.ParticleKernel`: Kernel for particle propagation
  * `referencing::BaytesFilters.ParticleReferencing`: Referencing method
  * `memory::BaytesFilters.ParticleFilterMemory`: Memory for observed and latent data in PF.
