```
sample(lds::LinearDynamicalSystem{S,O}, T_steps::Int, n_trials::Int) where {T<:Real, S<:GaussianStateModel{T}, O<:GaussianObservationModel{T}}
```

Sample from a Linear Dynamical System (LDS) model for multiple trials.

# Arguments

  * `lds::LinearDynamicalSystem{S,O}`: The Linear Dynamical System model.
  * `T_steps::Int`: The number of time steps to sample for each trial.
  * `n_trials::Int`: The number of trials to sample.=

# Returns

  * `x::Array{T, 3}`: The latent state variables. Dimensions: (latent*dim, T*Steps, n_trials)
  * `y::Array{T, 3}`: The observed data. Dimensions: (obs*dim, T*steps, n_trials)

# Examples

```julia
lds = GaussianLDS(obs_dim=4, latent_dim=3)
x, y = sample(lds, 10, 100)  # 10 trials, 100 time steps each
```
