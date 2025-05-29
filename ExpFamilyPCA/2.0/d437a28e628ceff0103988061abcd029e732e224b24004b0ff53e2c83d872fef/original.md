```
PoissonEPCA(indim::Integer, outdim::Integer; options::Options = Options())
```

Poisson EPCA.

# Arguments

  * `indim::Integer`: Dimension of the input space.
  * `outdim::Integer`: Dimension of the latent (output) space.
  * `options::Options`: Optional parameters.

# Returns

  * `epca`: An `EPCA` subtype for the Poisson distribution.
