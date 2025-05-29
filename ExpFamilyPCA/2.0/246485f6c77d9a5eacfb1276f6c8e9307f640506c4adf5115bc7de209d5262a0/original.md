```
ContinuousBernoulliEPCA(indim::Integer, outdim::Integer; options::Options = Options(μ = 0.5))
```

Continuous Bernoulli EPCA.

# Arguments

  * `indim::Integer`: Dimension of the input space.
  * `outdim::Integer`: Dimension of the latent (output) space.
  * `options::Options`: Optional parameters (default: `μ = 0.25`).

# Returns

  * `epca`: An `EPCA` subtype for the continuous Bernoulli distribution.
