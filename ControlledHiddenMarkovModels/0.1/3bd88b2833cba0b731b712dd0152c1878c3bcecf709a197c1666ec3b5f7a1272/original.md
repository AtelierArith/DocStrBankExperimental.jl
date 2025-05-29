```
AbstractControlledHiddenMarkovModel
```

Interface for Hidden Markov Models with arbitrary emissions and exogenous control variables.

# Required methods

  * [`nb_states(hmm, par)`](@ref)
  * [`initial_distribution(hmm, par)`](@ref)
  * [`transition_matrix(hmm, control, par)`](@ref)
  * [`transition_matrix!(P, hmm, control, par)`](@ref)
  * [`emission_parameters(hmm, control, par)`](@ref)
  * [`emission_parameters!(θ, hmm, control, par)`](@ref)
  * [`emission_distribution(hmm, s, θ)`](@ref)

# Optional methods

  * [`log_initial_distribution(hmm, par)`](@ref)
  * [`log_transition_matrix(hmm, control, par)`](@ref)
  * [`log_transition_matrix!(logP, hmm, control, par)`](@ref)

# Compatible with

  * [`rand(rng, hmm, control_sequence, par)`](@ref)
  * [`logdensityof(hmm, obs_sequence, control_sequence, par; safe)`](@ref)
  * [`infer_current_state(hmm, obs_sequence, control_sequence, par; safe)`](@ref)
