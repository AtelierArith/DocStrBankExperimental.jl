```
ExtendedKalmanFilter(kf, dynamics, measurement; Ajac, Cjac)
ExtendedKalmanFilter(dynamics, measurement, R1,R2,d0=MvNormal(Matrix(R1)); nu::Int, p = NullParameters(), α = 1.0, check = true)
```

A nonlinear state estimator propagating uncertainty using linearization.

The constructor to the extended Kalman filter takes dynamics and measurement functions, and either covariance matrices, or a [`KalmanFilter`](@ref). If the former constructor is used, the number of inputs to the system dynamics, `nu`, must be explicitly provided with a keyword argument.

By default, the filter will internally linearize the dynamics using ForwardDiff. User provided Jacobian functions can be provided as keyword arguments `Ajac` and `Cjac`. These functions should have the signature `(x,u,p,t)::AbstractMatrix` where `x` is the state, `u` is the input, `p` is the parameters, and `t` is the time.

The dynamics and measurement function are on the following form

```
x(t+1) = dynamics(x, u, p, t) + w
y      = measurement(x, u, p, t) + e
```

where `w ~ N(0, R1)`, `e ~ N(0, R2)` and `x(0) ~ d0`

The matrices `R1, R2` can be time varying such that, e.g., `R1[:, :, t]` contains the $R_1$ matrix at time index `t`. They can also be given as functions on the form

```
Rfun(x, u, p, t) -> R
```

This allows for, e.g., handling functions where the dynamics disturbance $w$ is an input argument to the function, by linearizing the dynamics w.r.t. the disturbance input in a function for $R_1$, like this (assuming the dynamics have the function signalture `f(x, u, p, t, w)`):

```
function R1fun(x,u,p,t)
    Bw = ForwardDiff.jacobian(w->f(x, u, p, t, w), zeros(length(w)))
    Bw * R1 * Bw'
end
```

When providing functions, the dimensions of the state, input and output, `nx, nu, ny` must be provided as keyword arguments to the `ExtendedKalmanFilter` constructor since these cannot be inferred from the function signature. For maximum performance, provide statically sized matrices from StaticArrays.jl

See also [`UnscentedKalmanFilter`](@ref) which is typically more accurate than `ExtendedKalmanFilter`. See [`KalmanFilter`](@ref) for detailed instructions on how to set up a Kalman filter `kf`.
