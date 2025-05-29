`perron_frobenius(markov_chain; step = 1)`

# Description

```
Calculate the perron-frobenius matrix from a markov chain.
```

# Arguments

  * `markov_chain::AbstractVector`: A vector of integers representing the state of a markov chain at each time step.

# Keyword Arguments

  * `step::Integer=1`: The step size of the constructed operator.

# Returns

  * `perron_frobenius_matrix::Matrix`: The perron-frobenius matrix of the markov chain.
