```
play([rng=Random.GLOBAL_RNG, ]brd, init_action_dist[, options=BROptions(); num_reps=1])
```

Return the action distribution after `num_reps` times iteration

# Arguments

  * `rng::AbstractRNG` : Random number generator used.
  * `brd::AbstractBRD` : `AbstractBRD` instance.
  * `init_action_dist::Vector{<:Integer}` : The initial distribution of players' actions.
  * `options::BROptions` : Options for `best_response` method.
  * `num_reps::Integer` : The number of iterations.

# Returns

  * `::Vector{<:Integer}` : The action distribution after iterations.
