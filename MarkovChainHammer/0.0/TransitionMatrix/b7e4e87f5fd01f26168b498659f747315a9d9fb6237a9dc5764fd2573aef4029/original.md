sparse*generator(markov*chain; dt = 1)

# Description

```
Calculate the generator matrix from a markov chain in sparse format
```

# Arguments

  * `markov_chain::AbstractVector`: A vector of integers representing the state of a markov chain at each time step.

# Keyword Arguments

  * `dt::Real=1`: The time step of the constructed operator.

# Returns

  * `generator_matrix::Matrix`: The generator matrix of the markov chain in sparse format
