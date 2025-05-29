```
init_sigma(rng, error; init_dist)
```

Initialization function for σ parameters based on the error model.

# Arguments

  * `rng::AbstractRNG`: Randomizer to use.
  * `error`: Error model. One of AdditiveError, ProportionalError, CombinedError, or CustomError.
  * `init_dist::Sampleable`: Distribution from which to sample the initial σ. Default = Uniform(0, 1)
