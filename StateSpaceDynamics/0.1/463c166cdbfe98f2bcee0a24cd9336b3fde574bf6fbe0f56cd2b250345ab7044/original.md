```
loglikelihood(x::Matrix{T}, lds::LinearDynamicalSystem{S,O}, y::Matrix{T}) where {T<:Real, S<:GaussianStateModel, O<:PoissonObservationModel}
```

Calculate the complete-data log-likelihood of a Poisson Linear Dynamical System model for a single trial. 

# Arguments

  * `x::Matrix{T}`: The latent state variables. Dimensions: (latent*dim, T*steps)
  * `lds::LinearDynamicalSystem{S,O}`: The Linear Dynamical System model.
  * `y::Matrix{T}`: The observed data. Dimensions: (obs*dim, T*steps)
  * `w::Vector{T}`: Weights for each observation in the log-likelihood calculation. Not currently used.

# Returns

  * `ll::T`: The log-likelihood value.

# Examples

```juliaestep!
lds = PoissonLDS(obs_dim=4, latent_dim=3)
x, y = sample(lds, 100, 1)  # 1 trial, 100 time steps
ll = loglikelihood(x, lds, y)
```
