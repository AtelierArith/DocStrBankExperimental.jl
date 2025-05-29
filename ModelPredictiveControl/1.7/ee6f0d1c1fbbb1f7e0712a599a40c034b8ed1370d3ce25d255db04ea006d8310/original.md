```
MovingHorizonEstimator(
    model, He, i_ym, nint_u, nint_ym, P̂_0, Q̂, R̂, Cwt=Inf;
    optim=default_optim_mhe(model), 
    gradient=AutoForwardDiff(),
    jacobian=AutoForwardDiff(),
    direct=true,
    covestim=default_covestim_mhe(model, i_ym, nint_u, nint_ym, P̂_0, Q̂, R̂; direct)
)
```

Construct the estimator from the augmented covariance matrices `P̂_0`, `Q̂` and `R̂`.

This syntax allows nonzero off-diagonal elements in $\mathbf{P̂_i}, \mathbf{Q̂, R̂}$, where $\mathbf{P̂_i}$ is the initial estimation covariance, provided by `P̂_0` argument. The keyword argument `covestim` also allows specifying a custom [`StateEstimator`](@ref) object for the estimation of covariance at the arrival $\mathbf{P̂}_{k-N_k}(k-N_k+p)$. The supported types are [`KalmanFilter`](@ref), [`UnscentedKalmanFilter`](@ref) and  [`ExtendedKalmanFilter`](@ref).
