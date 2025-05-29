```
DiscreteHomogeneousProcess
```

A discrete, homogeneous Poisson process.

The model supports Bayesian inference of the probabilistic model:

```
λ[i] ~ Gamma(λ[i] | α0, β0) (i = 1, ..., N)
x[i, t] ~ Poisson(x[i, t] | λ[i] * dt) (t = 1, ..., T)
```

# Arguments

  * `λ::Vector{Float64}`: a vector of intensities.
  * `α0::Float64`: the shape parameter of the Gamma prior.
  * `β0::Float64`: the inverse-scale (i.e., rate) parameter of the Gamma prior.
  * `dt::Float64`: the physical time represented by each time step, `t`.
