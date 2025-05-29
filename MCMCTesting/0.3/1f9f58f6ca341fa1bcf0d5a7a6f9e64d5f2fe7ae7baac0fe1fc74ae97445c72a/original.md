```
markovchain_transition(rng, model, kernel, θ, y)
```

Perform a single Markov chain transition of `kernel` on the previous state `θ` targeting the posterior of `model` conditioned on `y`.

# Arguments

  * `rng::Random.AbstractRNG`: Random number generator.
  * `model`: Model forming the posterior `p(θ|y)` conditioned on `y`.
  * `θ`: Previous state of the Markov chain.
  * `y`: Data to condition on.

# Returns

  * `θ′`: Next state of the Markov chain.
