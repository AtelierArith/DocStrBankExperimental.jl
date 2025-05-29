```
randmcmc([rng::AbstractRNG], kdpp::kDPP, N::Int; kwargs...)
```

MCMC sampling from a k-DPP [2].

## Arguments

  * `rng` : Random number generator (by default Random.GLOBAL_RNG is used)
  * `kdpp` : k-DeterminantalPointProcess
  * `N` : Number of samples

## Keyword Arguments

  * `init_state`
  * `return_final_state`
  * `mix_eps`
  * `mixing_steps`
  * `steps_between_samples`

TODO: 

  * Add support for running MCMC in parallel, similar as rand.
  * Make sure parallelization produces unbiased and consistent samples.
