```
GaussianEPCA(indim::Integer, outdim::Integer; options::Options = Options())
```

An EPCA model with Gaussian loss.

# Arguments

  * `indim::Integer`: Dimension of the input space.
  * `outdim::Integer`: Dimension of the latent (output) space.
  * `options::Options`: Optional parameters.

# Returns

  * `epca`: An EPCA subtype for the Gaussian distribution.
