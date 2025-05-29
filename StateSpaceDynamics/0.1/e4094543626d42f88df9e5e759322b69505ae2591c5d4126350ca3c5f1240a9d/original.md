```
PoissonLDS(; A, C, Q, log_d, x0, P0, refractory_period, fit_bool, obs_dim, latent_dim)
```

Construct a Linear Dynamical System with Gaussian state and Poisson observation models.

# Arguments

  * `A::Matrix{T}=Matrix{T}(undef, 0, 0)`: Transition matrix
  * `C::Matrix{T}=Matrix{T}(undef, 0, 0)`: Observation matrix
  * `Q::Matrix{T}=Matrix{T}(undef, 0, 0)`: Process noise covariance
  * `log_d::Vector{T}=Vector{T}(undef, 0)`: Mean firing rate vector (log space)
  * `x0::Vector{T}=Vector{T}(undef, 0)`: Initial state
  * `P0::Matrix{T}=Matrix{T}(undef, 0, 0)`: Initial state covariance
  * `refractory_period::Int=1`: Refractory period
  * `fit_bool::Vector{Bool}=fill(true, 7)`: Vector indicating which parameters to fit during optimization
  * `obs_dim::Int`: Dimension of the observations (required if C, D, or log_d is not provided.)
  * `latent_dim::Int`: Dimension of the latent state (required if A, Q, x0, P0, or C is not provided.)
