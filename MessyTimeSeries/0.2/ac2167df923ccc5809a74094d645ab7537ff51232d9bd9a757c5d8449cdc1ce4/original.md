```
KalmanSettings(Y::Union{FloatMatrix, JMatrix{Float64}}, B::FloatMatrix, R::Union{UniformScaling{Float64}, SymMatrix}, C::FloatMatrix, D::FloatMatrix, Q::SymMatrix, X0::FloatVector, P0::SymMatrix; kwargs...)
```

`KalmanSettings` constructor.

# Arguments

  * `Y`: Observed measurements (`nxT`)
  * `B`: Measurement equations' coefficients
  * `R`: Covariance matrix of the measurement equations' error terms
  * `C`: Transition equations' coefficients
  * `D`: Transition equations' coefficients associated to the error terms
  * `Q`: Covariance matrix of the transition equations' error terms
  * `X0`: Mean vector for the states at time $t=0$
  * `P0`: Covariance matrix for the states at time $t=0$

# Keyword arguments

  * `compute_loglik`: Boolean (`true` for computing the loglikelihood in the Kalman filter - default: `true`)
  * `store_history`: Boolean (`true` to store the history of the filter and smoother - default: `true`)
