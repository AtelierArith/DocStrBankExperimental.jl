```
TemperedSampler <: AbstractMCMC.AbstractSampler
```

A `TemperedSampler` struct wraps a sampler upon which to apply the Parallel Tempering algorithm.

# Fields

  * `sampler`: sampler(s) used to target the tempered distributions
  * `chain_to_beta`: collection of inverse temperatures β; β[i] correponds i-th tempered model
  * `swapstrategy`: strategy to use for swapping
  * `adapt`: boolean flag specifying whether or not to adapt
  * `adaptation_states`: adaptation parameters
