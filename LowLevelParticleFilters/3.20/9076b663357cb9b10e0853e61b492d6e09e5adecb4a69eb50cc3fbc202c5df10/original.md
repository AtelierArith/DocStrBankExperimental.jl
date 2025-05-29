```
R = double_integrator_covariance(Ts, σ2=1)
```

Returns the covariance matrix of a discrete-time integrator with piecewise constant stochastic force as input. Assumes the state [x; ẋ]. `Ts` is the sample time. `σ2` scales the covariance matrix with the variance of the noise.

This matrix is rank deficient and some applications might require a small increase in the diagonal to make it positive definite (or use [`double_integrator_covariance_smooth`](@ref)).

See also [`double_integrator_covariance_smooth`](@ref) for the version that does not assume piecewise constant noise, leading to a full-rank covariance matrix that results in sample-tiem invariant covariance dynamics (often favorable).
