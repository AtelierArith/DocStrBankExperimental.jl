```
tempered_sample([rng, ], model, sampler, N, inverse_temperatures; kwargs...)
OR
tempered_sample([rng, ], model, sampler, N, N_it; swap_strategy=SingleSwap(), kwargs...)
```

Generate `N` samples from `model` using a tempered version of the provided `sampler`. Provide either `inverse_temperatures` or `N_it` (and a `swap_strategy`) to generate some

# Keyword arguments

  * `N_burnin::Integer` burn-in steps will be carried out before any swapping between chains is attempted
  * `swap_strategy::AbstractSwapStrategy` specifies the method for swapping inverse temperatures between chains
  * `steps_per_swap::Integer` steps are carried out between each attempt at a swap

# See also

  * [`tempered`](@ref)
  * [`TemperedSampler`](@ref)
  * For more on the swap strategies:

      * [`AbstractSwapStrategy`](@ref)
      * [`ReversibleSwap`](@ref)
      * [`NonReversibleSwap`](@ref)
      * [`SingleSwap`](@ref)
      * [`SingleRandomSwap`](@ref)
      * [`RandomSwap`](@ref)
      * [`NoSwap`](@ref)
