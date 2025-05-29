```
ergodic_probs(P::Matrix{Float64})
```

Returns a `k`-size Vector of ergodic probabilites of each state.     

The ergodic probabilites (also known as long-term probabilites) of a Markov process are the probabilites that satisfy the following equation:

$$
\lim_{n\to\infty} P^n = \pi = P \pi 
$$

The ergodic probability is proportional to the eigenvector of the transition matrix P associated to the unit eigenvalue.

# Arguments

  * `P::Matrix{Float64}`: left stochastic transition matrix.

See also [`expected_duration`](@ref).
