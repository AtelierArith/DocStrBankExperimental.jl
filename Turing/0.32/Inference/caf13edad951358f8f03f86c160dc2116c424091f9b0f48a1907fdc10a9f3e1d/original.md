```julia
struct PG{space, R} <: Turing.Inference.ParticleInference
```

Particle Gibbs sampler.

# Fields

  * `nparticles::Int64`: Number of particles.
  * `resampler::Any`: Resampling algorithm.
