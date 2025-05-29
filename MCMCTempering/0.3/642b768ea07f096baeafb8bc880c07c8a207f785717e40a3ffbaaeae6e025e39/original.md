```
tempered(sampler, inverse_temperatures; kwargs...)
OR
tempered(sampler, num_temps; swap_strategy=ReversibleSwap(), kwargs...)
```

Return a tempered version of `sampler` using the provided `inverse_temperatures` or inverse temperatures generated from `num_temps` and the `swap_strategy`.

# Arguments

  * `sampler` is an algorithm or sampler object to be used for underlying sampling and to apply tempering to
  * The temperature schedule can be defined either explicitly or just as an integer number of temperatures, i.e. as:

      * `inverse_temperatures` containing a sequence of 'inverse temperatures' {β₀, ..., βₙ} where 0 ≤ βₙ < ... < β₁ < β₀ = 1     OR
      * `num_temps`, specifying the integer number of inverse temperatures to include in a generated `inverse_temperatures`

# Keyword arguments

  * `swap_strategy::AbstractSwapStrategy` specifies the method for swapping inverse temperatures between chains
  * `steps_per_swap::Integer` steps are carried out between each attempt at a swap

# See also

  * [`TemperedSampler`](@ref)
  * For more on the swap strategies:

      * [`AbstractSwapStrategy`](@ref)
      * [`ReversibleSwap`](@ref)
      * [`NonReversibleSwap`](@ref)
      * [`SingleSwap`](@ref)
      * [`SingleRandomSwap`](@ref)
      * [`RandomSwap`](@ref)
      * [`NoSwap`](@ref)
