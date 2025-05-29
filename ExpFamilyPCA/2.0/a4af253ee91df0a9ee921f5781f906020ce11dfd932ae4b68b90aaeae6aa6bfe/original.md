```
BernoulliEPCA(indim::Integer, outdim::Integer; options = Options(μ = 0.5))
```

Bernoulli EPCA.

# Arguments

  * `indim::Integer`: Dimension of the input space.
  * `outdim::Integer`: Dimension of the latent (output) space.
  * `options::Options`: Optional parameters (default: `μ = 0.5`).

# Returns

  * `epca`: An `EPCA` subtype for the Bernoulli distribution.
