```
SmootherOutput{NamedTuple}
```

Container for outputs from the Quadratic Kalman Smoother.

# Fields

  * `Z_smooth::Matrix{T}`: Smoothed states (P × (T̄+1))
  * `P_smooth::Array{T,3}`: Smoothed covariances (P × P × (T̄+1))
