# Basic use:

```
q, logev = VI(logp, μ, σ²=0.1; S = 100, iterations = 1, show_every = -1)
```

Returns approximate Gaussian posterior and log evidence.

# Arguments

A description of only the most basic arguments follows.

  * `logp` is a function that expresses the (unnormalised) log-posterior, i.e. joint log-likelihood.
  * `μ` is the initial mean of the approximating Gaussian posterior.
  * `σ²` specifies the initial covariance of the approximating Gaussian posterior as σ² * I . Default value is `0.1`.
  * `S` is the number of drawn samples that approximate the lower bound integral.
  * `iterations` specifies for how many iterations to run optimisation on the lower bound (elbo).
  * `show_every`: report progress every `show_every` number of iterations.

# Outputs

  * `q` is the approximating posterior returned as a `Distributions.MvNormal` type
  * `logev` is the approximate log-evidence.

# Example

```julia-repl
# infer posterior of Bayesian linear regression, compare to exact result
julia> using LinearAlgebra, Distributions
julia> D = 4; X = randn(D, 1000); W = randn(D); β = 0.3; α = 1.0;
julia> Y = vec(W'*X); Y += randn(size(Y))/sqrt(β);
julia> Sn = inv(α*I + β*(X*X')) ; mn = β*Sn*X*Y; # exact posterior
julia> posterior, logev = VI( w -> logpdf(MvNormal(vec(w'*X), sqrt(1/β)), Y) + logpdf(MvNormal(zeros(D),sqrt(1/α)), w), randn(D); S = 1_000, iterations = 15);
julia> display([mean(posterior) mn])
julia> display([cov(posterior)  Sn])
julia> display(logev) # display negative log evidence
```
