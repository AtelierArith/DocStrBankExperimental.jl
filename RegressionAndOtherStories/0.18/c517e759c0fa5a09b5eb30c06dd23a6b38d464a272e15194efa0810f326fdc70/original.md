Compute logprobability values for a set of observation values.

```julia
logprob(ndf, mass, obs, sigma, k)

```

## Required arguments

  * `ndf::DataFrame`: *Nested* dataframe with parameter set b (b.1, b.2, ...)
  * `mass::Matrix{Floats64}`: Values os size(no of obs, length of b)
  * `obs`: Observation values
  * `sigma::Vector{Float64}`: Sigma values used in logpdf calculation
  * `k::Int`: Length of b vactor

## Return values

Vector{Float64} of logpdf values
