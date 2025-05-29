```julia
struct SMC{space, R} <: Turing.Inference.ParticleInference
```

Sequential Monte Carlo sampler.

# Fields

  * `resampler::Any`
