```
KalmanSettings(Y::Union{FloatMatrix, JMatrix{Float64}}, B::FloatMatrix, R::Union{UniformScaling{Float64}, SymMatrix}, C::FloatMatrix, Q::SymMatrix; kwargs...)
```

`KalmanSettings` constructor.

# Arguments

  * `Y`: Observed measurements (`nxT`)
  * `B`: Measurement equations' coefficients
  * `R`: Covariance matrix of the measurement equations' error terms
  * `C`: Transition equations' coefficients
  * `Q`: Covariance matrix of the transition equations' error terms

# Keyword arguments

  * `compute_loglik`: Boolean (`true` for computing the loglikelihood in the Kalman filter - default: `true`)
  * `store_history`: Boolean (`true` to store the history of the filter and smoother - default: `true`)

# Notes

This particular constructor sets `D` to be an identity matrix, `X0` to be a vector of zeros and computes `P0` via `solve_discrete_lyapunov(C, Q)`.
