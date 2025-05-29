```
SmootherOutput{T<:Real}
```

Container for outputs from the Quadratic Kalman Smoother. This structure encapsulates the results produced by the smoothing algorithm, which refines state estimates by incorporating information from both past and future observations. The smoother typically yields more accurate state estimates and associated uncertainty quantification than the filter alone.

# Fields

  * `Z_smooth::Matrix{T}`: A matrix containing the smoothed state estimates. The matrix dimensions are P × (T̄+1), where P represents the dimension of the state vector and T̄+1 denotes the number of time steps.
  * `P_smooth::Array{T,3}`: A three-dimensional array holding the smoothed covariance matrices. Each slice P_smooth[:, :, t] corresponds to the covariance estimate for the state at time step t, with overall dimensions P × P × (T̄+1).

# Details

The smoothed states and covariances are calculated using the Quadratic Kalman Smoother, which enhances the filtering results by backward recursion. This allows for improved state estimation by considering future as well as past measurements. The structure is essential for diagnostic checks and subsequent analyses in applications where state estimation uncertainty plays a critical role.
