```
samples(bm, nsamples; ...)
```

Generates `nsamples` samples from a Boltzmann machine model `bm` by running a Gibbs sampler. This can also be used for sampling from a *conditional distribution* (see argument `conditions` below.)

# Optional keyword arguments:

  * `burnin`: Number of Gibbs sampling steps, defaults to 50.
  * `conditions`: `Vector{Pair{Int,Float64}}`, containing pairs of variables and their values that are to be conditioned on. E. g. `[1 => 1.0, 3 => 0.0]`
  * `samplelast`: boolean to indicate whether to sample in last step (true, default) or whether to use the activation potential.
