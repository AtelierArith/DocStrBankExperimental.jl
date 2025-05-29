```
random_stochastic_matrix([rng], n[, k])
```

Return a randomly sampled `n x n` stochastic matrix with `k` nonzero entries for each row.

# Arguments

  * `rng::AbstractRNG=GLOBAL_RNG` : Random number generator.
  * `n::Integer` : Number of states.
  * `k::Integer=n` : Number of nonzero entries in each column of the matrix. Set to `n` if none specified.

# Returns

  * `p::Array` : Stochastic matrix.
