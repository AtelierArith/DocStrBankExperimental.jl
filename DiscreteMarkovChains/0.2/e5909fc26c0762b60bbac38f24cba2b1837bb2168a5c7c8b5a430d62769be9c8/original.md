```
probability_matrix(x)
```

# Definitions

The one-step transition matrix, $T$, of a Markov chain, $\{X_t\}$ is a matrix whose $(i,j)$th entry is the probability of the process being in state $j$ at time 1 given that the process started in state $i$ at time 0. That is

$$
T = \{\{p^{(1)}_{i,j}\}\}_{i,j ∈ S} = \{\{\mathbb{P}(X_1=j | X_0=i)\}\}_{i,j ∈ S}
$$

where $S$ is the state space of $\{X_t\}$.

# Arguments

  * `x`: some kind of Markov chain.

# Returns

The one-step probability matrix of the Markov chain.
