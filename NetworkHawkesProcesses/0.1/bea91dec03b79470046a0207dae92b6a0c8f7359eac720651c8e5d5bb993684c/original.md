ExponentialImpulseResponse

An exponential impulse response function with Gamma prior.

This model is a building block for Hawkes processes. Given a number of child events on node `j` attributed to node `i`, it generates event times according to a exponential distribution with rate parameter `θ[i, j]`.

For Bayesian inference we assume a uniform Gamma priors for `θ`:

```
`θ[i, j] ~ Gamma(κ, ν) for all i, j`
```

The resulting model is only conjugate in the limit as the sampling duration approaches infinity, however. Thus, Bayesian inference for the exponential process is approximate.

# Arguments

  * `θ::Float64`: the rate of the exponential distribution (i.e., `1 / scale`).
  * `α`: shape parameter of Gamma prior for `θ` (default: 1.0).
  * `β`: rate parameter of Gamma prior for `θ` (default: 1.0).
