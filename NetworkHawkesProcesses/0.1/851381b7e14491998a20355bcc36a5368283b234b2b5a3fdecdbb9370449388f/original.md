```
DiscreteLogGaussianCoxProcess
```

A discrete log Gaussian Cox process constructed from a realization of a Gaussian process at fixed gridpoints.

The probabilistic model is:

```
y ~ GP(0, K)
λ[t] = exp(m + y[t])
s ~ PP(λ[t])
```

For an arbitrary set of gridpoints, `x[1] = 1, ..., x[N] = T`, a corresponding sample of the Gaussian process, `y[1], ..., y[N]`, has a `N(0, Σ)` distribution, where

```
Σ[i, j] = K(x[i], x[j])
```

The process is sampled by interpolating between intensity values `λ[1], ..., λ[N]`.

# Arguments

  * `x::Vector{Int64}`: a strictly increasing vector of sampling gridpoints.
  * `λ::Matrix{Float64}`: a non-negative, `T x N` intensity matrix, ie, `λ[i, n] = λ_n([x[i])`.
  * `Σ::Matrix{Float64}`: a positive-definite variance matrix.
  * `m::Float64`: intensity offset equal to `log(λ0)` of a homogeneous process.
