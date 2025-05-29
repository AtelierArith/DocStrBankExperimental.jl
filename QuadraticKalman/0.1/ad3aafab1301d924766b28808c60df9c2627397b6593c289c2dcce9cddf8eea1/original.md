```
Moments{T<:Real}
```

Unconditional Moments Structure for the Quadratic Kalman Filter.

This structure encapsulates the long-run (stationary) moments of both the state and the augmented state. These moments include the mean and covariance estimates, which are critical for initializing the filter and for conducting diagnostic evaluations of the model dynamics.

Fields:

  * state_mean::AbstractVector{T}: Unconditional (stationary) mean vector of the state.
  * state_cov::AbstractMatrix{T}: Unconditional covariance matrix of the state.
  * aug_mean::AbstractVector{T}: Unconditional mean vector of the augmented state.
  * aug_cov::AbstractMatrix{T}: Unconditional covariance matrix of the augmented state.
