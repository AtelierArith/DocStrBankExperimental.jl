```
sample_joint(rng, model)
```

Sample from the joint distribution of the prior and the predictive distribution of `model`.

# Arguments

  * `rng::Random.AbstractRNG`: Random number generator.
  * `model`: Model subject to test.

# Returns

  * `θ`: Model parameter sampled from the prior `p(θ)`.
  * `y`: Data generated from conditionally on `θ` from `p(y|θ)`
