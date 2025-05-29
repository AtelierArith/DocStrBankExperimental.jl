```
is_reversible(x)
```

# Definitions

A Markov chain is said to be reversible if it satisfies the equation $π_i p_{ij} = π_j p_{ji}$ where $π$ is the stationary distribution and $p$ are the elements of the transition matrix of the Markov chain.

# Arguments

  * `x`: some kind of Markov chain.

# Returns

`true` if the Markov chain is reversible.
