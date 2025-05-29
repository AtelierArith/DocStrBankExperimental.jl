`generator(markov_chain; dt=1)`

# Description

```
Calculate the generator matrix from a markov chain.
```

# Arguments

  * `markov_chain::AbstractVector`: A vector of integers representing the state of a markov chain at each time step.
  * `dt::Real`: The time step between each state.

# Returns

  * `generator_matrix::Matrix`: The generator matrix of the markov chain.
