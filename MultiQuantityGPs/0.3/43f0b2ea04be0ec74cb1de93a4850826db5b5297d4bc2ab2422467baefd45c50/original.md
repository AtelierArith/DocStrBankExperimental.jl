Inputs:

  * `X`: a single sample input or an array of multiple
  * `full_cov`: (optional) if this is true, returns the full covariance matrix in place of the vector of standard deviations

Outputs:

  * `μ, σ`: a pair of expected value(s) and uncertainty(s) for the given point(s)

# Examples

```julia
X = [([.1, .2], 1),
     ([.2, .1], 2)]
μ, σ = beliefModel(X) # result: [μ1, μ2], [σ1, σ2]
```
