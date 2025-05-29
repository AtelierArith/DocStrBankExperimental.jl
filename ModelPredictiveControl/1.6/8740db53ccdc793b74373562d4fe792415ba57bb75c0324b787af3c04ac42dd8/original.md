```
setmodel!(estim::StateEstimator, model=estim.model; <keyword arguments>) -> estim
```

Set `model` and covariance matrices of `estim` [`StateEstimator`](@ref).

Allows model adaptation of estimators based on [`LinModel`](@ref) at runtime. Modification  of [`NonLinModel`](@ref) state-space functions is not supported. New covariance matrices can be specified with the keyword arguments (see [`SteadyKalmanFilter`](@ref) documentation for the nomenclature). Not supported by [`Luenberger`](@ref) and [`SteadyKalmanFilter`](@ref),  use the time-varying [`KalmanFilter`](@ref) instead. The [`MovingHorizonEstimator`](@ref) model is kept constant over the estimation horizon $H_e$. The matrix dimensions and sample time must stay the same. Note that the observability and controllability of the new augmented model is not verified (see Extended Help for more info).

# Arguments

!!! info
    Keyword arguments with *`emphasis`* are non-Unicode alternatives.


  * `estim::StateEstimator` : estimator to set model and covariances.
  * `model=estim.model` : new plant model (not supported by [`NonLinModel`](@ref)).
  * `Q̂=nothing` or *`Qhat`* : new augmented model $\mathbf{Q̂}$ covariance matrix.
  * `R̂=nothing` or *`Rhat`* : new augmented model $\mathbf{R̂}$ covariance matrix.

# Examples

```jldoctest
julia> kf = KalmanFilter(LinModel(ss(0.1, 0.5, 1, 0, 4.0)), σQ=[√4.0], σQint_ym=[√0.25]);

julia> kf.model.A[], kf.Q̂[1, 1], kf.Q̂[2, 2] 
(0.1, 4.0, 0.25)

julia> setmodel!(kf, LinModel(ss(0.42, 0.5, 1, 0, 4.0)), Q̂=[1 0;0 0.5]);

julia> kf.model.A[], kf.Q̂[1, 1], kf.Q̂[2, 2] 
(0.42, 1.0, 0.5)
```

# Extended Help

!!! details "Extended Help"
    Using the default model augmentation computed by the [`default_nint`](@ref) method,  switching from a non-integrating plant model to an integrating one will produce an augmented model that is not observable. Moving the unmeasured disturbances at the  model input (`nint_u` parameter) can fix this issue.

