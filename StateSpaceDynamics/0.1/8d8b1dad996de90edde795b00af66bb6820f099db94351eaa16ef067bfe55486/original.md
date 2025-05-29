```
smooth(lds::LinearDynamicalSystem{S,O}, y::Array{T,3}) where {T<:Real, S<:GaussianStateModel{T}, O<:GaussianObservationModel{T}}
```

This function performs direct smoothing for a linear dynamical system (LDS) given the system parameters and the observed data for multiple trials.

# Arguments

  * `lds::LinearDynamicalSystem{S,O}`: The LDS object representing the system parameters.
  * `y::Array{T,3}`: The observed data array with dimensions (obs*dim, tiem*steps, n_trials).

# Returns

  * `x::Array{T,3}`: The optimal state estimates with dimensions (n*trials, time*steps, latent_dim).
  * `p_smooth::Array{T,4}`: The posterior covariance matrices with dimensions (latent*dim, latent*dim, time*steps, n*trials).
  * `inverse_offdiag::Array{T,4}`: The inverse off-diagonal matrices with dimensions (latent*dim, latent*dim, time*steps, n*trials).

# Example

```julia
lds = GaussianLDS(obs_dim=4, latent_dim=3)
y = randn(5, 100, 4)  # 5 trials, 100 time steps, 4 observed dimension
x, p_smooth, inverse_offdiag = smooth(lds, y)
```
