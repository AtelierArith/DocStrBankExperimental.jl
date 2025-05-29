```
GaussianLDS(; A, C, Q, R, x0, P0, fit_bool, obs_dim, latent_dim)
```

Construct a Linear Dynamical System with Gaussian state and observation models.

# Arguments

  * `A::Matrix{T}=Matrix{T}(undef, 0, 0)`: Transition matrix
  * `C::Matrix{T}=Matrix{T}(undef, 0, 0)`: Observation matrix
  * `Q::Matrix{T}=Matrix{T}(undef, 0, 0)`: Process noise covariance
  * `R::Matrix{T}=Matrix{T}(undef, 0, 0)`: Observation noise covariance
  * `x0::Vector{T}=Vector{T}(undef, 0)`: Initial state
  * `P0::Matrix{T}=Matrix{T}(undef, 0, 0)`: Initial state covariance
  * `fit_bool::Vector{Bool}=fill(true, 6)`: Vector indicating which parameters to fit during optimization
  * `obs_dim::Int`: Dimension of the observations (required if C or R is not provided.)
  * `latent_dim::Int`: Dimension of the latent state (required if A, Q, x0, P0, or C is not provided.)
