```
random_discrete_dp([rng], num_states, num_actions[, beta];
                   k=num_states, scale=1)
```

Generate a DiscreteDP randomly. The reward values are drawn from the normal distribution with mean 0 and standard deviation `scale`.

# Arguments

  * `rng::AbstractRNG=GLOBAL_RNG` : Random number generator.
  * `num_states::Integer` : Number of states.
  * `num_actions::Integer` : Number of actions.
  * `beta::Real=rand(rng)` : Discount factor. Randomly chosen from `[0, 1)` if not specified.
  * `;k::Integer(num_states)` : Number of possible next states for each state-action pair. Equal to `num_states` if not specified.
  * `scale::Real(1)` : Standard deviation of the normal distribution for the reward values.

# Returns

  * `ddp::DiscreteDP` : An instance of DiscreteDP.
