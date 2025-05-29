LogGaussianCoxProcess

A log Gaussian Cox process constructed from a realization of a Gaussian process at fixed gridpoints.

The model is

```
y ~ GP(0, K)
λ(t) = exp(m + y(t))
s ~ PP(λ(t))
```

For an arbitrary set of gridpoints, `x[1], ..., x[N]`, a corresponding sample of the Gaussian process, `y[1], ..., y[N]`, has a `N(0, Σ)` distribution, where

```
Σ[i, j] = K(x[i], x[j])
```

The process is sampled by interpolating between intensity values `λ[1], ..., λ[N]`.

# Arguments

  * `x::Vector{Float64}`: a strictly increasing vectors of sampling grid points.
  * `λ::Vector{Vector{Float64}}`: a list of non-negative intensity vectors such that `λ[k][i] = λ[k]([x[i])`.
  * `Σ::Matrix{Float64}`: a positive-definite variance matrix.
  * `m::Vector{Float64}`: intensity offsets equal to `log(λ0)` of homogeneous processes.
