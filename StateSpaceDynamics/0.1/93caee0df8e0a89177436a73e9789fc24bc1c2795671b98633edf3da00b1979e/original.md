```
smooth(lds::LinearDynamicalSystem{S,O}, y::Matrix{T}) where {T<:Real, S<:GaussianStateModel{T}, O<:GaussianObservationModel{T}}
```

This function performs direct smoothing for a linear dynamical system (LDS) given the system parameters and the observed data.

# Arguments

  * `lds::LinearDynamicalSystem{S,O}`: The LDS object representing the system parameters.
  * `y::Matrix{T}`: The observed data matrix.
  * `w::Vector{Float64}`: coeffcients to weight the data.

# Returns

  * `x::Matrix{T}`: The optimal state estimate.
  * `p_smooth::Array{T, 3}`: The posterior covariance matrix.
  * `inverse_offdiag::Array{T, 3}`: The inverse off-diagonal matrix.
  * `Q_val::T`: The Q-function value.

# Example

```julia
lds = GaussianLDS(obs_dim=4, latent_dim=3)
y = randn(100, 4)  # 100 time steps, 4 observed dimensions
x, p_smooth, inverse_offdiag, Q_val = DirectSmoother(lds, y)
```
