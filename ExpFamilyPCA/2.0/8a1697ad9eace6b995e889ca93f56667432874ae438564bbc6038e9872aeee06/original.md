```
BinomialEPCA(indim::Integer, outdim::Integer, n::Integer; options::Options = Options(μ = 0.5))
```

Binomial EPCA.

# Arguments

  * `indim::Integer`: Dimension of the input space.
  * `outdim::Integer`: Dimension of the latent (output) space.
  * `n::Integer`: A known parameter representing the number of trials (nonnegative).
  * `options::Options`: Optional parameters (default: `μ = 0.5`).

# Returns

  * `epca`: An `EPCA` subtype for the binomial distribution.
