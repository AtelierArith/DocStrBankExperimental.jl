```
IteratedExtendedKalmanFilter(kf, dynamics, measurement; Ajac, Cjac, step, maxiters, epsilon)
IteratedExtendedKalmanFilter(dynamics, measurement, R1,R2,d0=SimpleMvNormal(Matrix(R1)); nu::Int, ny=size(R2,1), Cjac = nothing, step = 1.0, maxiters=10, epsilon=1e-8)
```

A nonlinear state estimator propagating uncertainty using linearization. Returns an `ExtendedKalmanFilter` object but with Gauss-Newton based iterating measurement correction step.

The constructor to the iterated version of extended Kalman filter takes dynamics and measurement functions, and either covariance matrices, or a [`KalmanFilter`](@ref). If the former constructor is used, the number of inputs to the system dynamics, `nu`, must be explicitly provided with a keyword argument.

By default, the filter will internally linearize the dynamics using ForwardDiff. User provided Jacobian functions can be provided as keyword arguments `Ajac` and `Cjac`. These functions should have the signature `(x,u,p,t)::AbstractMatrix` where `x` is the state, `u` is the input, `p` is the parameters, and `t` is the time.

The dynamics and measurement function are of the following form

```
x(t+1) = dynamics(x, u, p, t) + w
y      = measurement(x, u, p, t) + e
```

where `w ~ N(0, R1)`, `e ~ N(0, R2)` and `x(0) ~ d0`

  * `step` is the step size for the Gauss-Newton iterations. Float between 0 and 1. Default is 1.0 which should be good enough for most applications. For more challenging applications, a smaller step size might be necessary.
  * `maxiters` is the maximum number of iterations. Default is 10. Usually a small number of iterations is needed. If higher number is needed, consider using UKF.
  * `epsilon` is the convergence criterion. Default is 1e-8

See also [`UnscentedKalmanFilter`](@ref) which is more robust than `IteratedExtendedKalmanFilter`. See [`KalmanFilter`](@ref) for detailed instructions on how to set up a Kalman filter `kf`.
