LogitNormalImpulseResponse

A logit-normal impulse response function.

This model is a building block for Hawkes process. Given a number of child events on node `j` attributed to node `i`, it generates event times according to a stretched logit-normal distribution with location parameter `μ[i, j]`, precision parameter `τ[i, j]`, and support `[0, Δtmax]`.

For Bayesian inference we assume a uniform normal-gamma prior for `μ` and `τ`:

```
`τ[i, j] ~ Gamma(α0, β0)` for all i, j
`μ[i, j] | σ[i, j] ~ Normal(μ[i, j], σ[i, j])` for all i, j
```

where `σ[i,, j] = 1 / sqrt(κ[i, j] * τ[i, j])` for all i, j.

# Arguments

  * `μ::Float64`: the location of the logit-normal distribution.
  * `τ::Float64`: the precision of the logit-normal distribution (i.e., `1 / σ^2`).
  * `μμ::Float64`: the location of the normal prior for `μ` (default: 1.0).
  * `κμ::Float64`: the precision multiplier of the normal prior for `μ` (default: 1.0).
  * `α`: shape parameter of gamma prior for `τ` (default: 1.0).
  * `β`: rate parameter of gamma prior for `τ` (default: 1.0).
  * `Δtmax::Float64`: the upperbound of the process support, `[0, Δtmax]`.
