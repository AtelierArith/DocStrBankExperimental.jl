```
loglikelihood(x::Array{T, 3}, lds::LinearDynamicalSystem{S,O}, y::Array{T, 3}) where {T<:Real, S<:GaussianStateModel{T}, O<:PoissonObservationModel{T}}
```

Calculate the complete-data log-likelihood of a Poisson Linear Dynamical System model for multiple trials.

# Arguments

  * `x::Array{T, 3}`: The latent state variables. Dimensions: (latent*dim, T*Steps, n_trials)
  * `lds::LinearDynamicalSystem{S,O}`: The Linear Dynamical System model.
  * `y::Array{T, 3}`: The observed data. Dimensions: (obs*dim, T*steps, n_trials)

# Returns

  * `ll::T`: The log-likelihood value.

# Examples

```julia
lds = PoissonLDS(obs_dim=4, latent_dim=3)
x, y = sample(lds, 100, 10)  # 10 trials, 100 time steps each
ll = loglikelihood(x, lds, y)
```
