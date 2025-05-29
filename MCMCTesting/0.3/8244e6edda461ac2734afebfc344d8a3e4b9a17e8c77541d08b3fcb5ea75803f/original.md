```
sample_predictive(rng, model, θ)
```

Sample from the predictive distribution of `model` conditionally on `θ`

# Arguments

  * `rng::Random.AbstractRNG`: Random number generator.
  * `model`: Model subject to test.
  * `θ`: Model parameters to condition on.

# Returns

  * `y`: Data generated from conditionally on `θ` from `p(y|θ)`
