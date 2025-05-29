```
play([rng=Random.GLOBAL_RNG,] ld, init_actions[; num_reps=1])
```

Return new action profile after `num_reps` iterations.

# Arguments

  * `rng::AbstractRNG` : Random number generator used.
  * `ld::LogitDynamics{N}` : `LogitDynamics` instance.
  * `init_actions::PureActionProfile` : Initial action profile.
  * `num_reps::Integer` : The number of iterations.

# Returns

  * `::Vector{<:Integer}` : New action profile.
