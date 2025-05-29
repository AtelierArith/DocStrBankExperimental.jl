```
AbstractHiddenMarkovModel
```

Interface for Hidden Markov Models with arbitrary emissions.

# Required methods

  * [`nb_states(hmm, par)`](@ref)
  * [`initial_distribution(hmm, par)`](@ref)
  * [`transition_matrix(hmm, par)`](@ref)
  * [`emission_distribution(hmm, s, par)`](@ref)

# Optional methods

  * [`log_initial_distribution(hmm, par)`](@ref)
  * [`log_transition_matrix(hmm, par)`](@ref)

# Compatible with

  * [`rand(rng, hmm, T, par)`](@ref)
  * [`logdensityof(hmm, obs_sequence, par; safe)`](@ref)
  * [`infer_current_state(hmm, obs_sequence, par; safe)`](@ref)
