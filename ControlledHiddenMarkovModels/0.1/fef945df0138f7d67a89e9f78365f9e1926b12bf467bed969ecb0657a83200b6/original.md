```
HiddenMarkovModel{R1,R2,D}
```

Concrete subtype of [`AbstractHMM`](@ref) which stores the state and observation parameters directly.

# Fields

  * `p0::Vector{R1}`
  * `P::Matrix{R2}`
  * `emissions::Vector{D}`

# Compatible with

  *   * [`baum_welch_multiple_sequences(obs_sequences, hmm_init, par; kwargs...)`](@ref)
  *   * [`baum_welch(obs_sequence, hmm_init, par; kwargs...)`](@ref)
