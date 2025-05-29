```
KalmanFilter(model::LinModel; <keyword arguments>)
```

Construct a time-varying Kalman Filter with the [`LinModel`](@ref) `model`.

The process model is identical to [`SteadyKalmanFilter`](@ref). The matrix $\mathbf{P̂}$ is the estimation error covariance of `model` states augmented with the stochastic ones (specified by `nint_u` and `nint_ym`). Three keyword arguments specify its initial value with $\mathbf{P̂}_{-1}(0) = \mathrm{diag}\{ \mathbf{P}(0), \mathbf{P_{int_{u}}}(0),  \mathbf{P_{int_{ym}}}(0) \}$. The initial state estimate $\mathbf{x̂}_{-1}(0)$ can be manually specified with [`setstate!`](@ref), or automatically with [`initstate!`](@ref). This estimator is allocation-free.

# Arguments

!!! info
    Keyword arguments with *`emphasis`* are non-Unicode alternatives.


  * `model::LinModel` : (deterministic) model for the estimations.
  * `i_ym=1:model.ny` : `model` output indices that are measured $\mathbf{y^m}$, the rest    are unmeasured $\mathbf{y^u}$.
  * `σP_0=fill(1/model.nx,model.nx)` or *`sigmaP_0`* : main diagonal of the initial estimate   covariance $\mathbf{P}(0)$, specified as a standard deviation vector.
  * `σQ=fill(1/model.nx,model.nx)` or *`sigmaQ`* : main diagonal of the process noise   covariance $\mathbf{Q}$ of `model`, specified as a standard deviation vector.
  * `σR=fill(1,length(i_ym))` or *`sigmaR`* : main diagonal of the sensor noise covariance   $\mathbf{R}$ of `model` measured outputs, specified as a standard deviation vector.
  * `nint_u=0`: integrator quantity for the stochastic model of the unmeasured disturbances at   the manipulated inputs (vector), use `nint_u=0` for no integrator.
  * `nint_ym=default_nint(model,i_ym,nint_u)` : same than `nint_u` but for the unmeasured    disturbances at the measured outputs, use `nint_ym=0` for no integrator.
  * `σQint_u=fill(1,sum(nint_u))` or *`sigmaQint_u`* : same than `σQ` but for the unmeasured   disturbances at manipulated inputs $\mathbf{Q_{int_u}}$ (composed of integrators).
  * `σPint_u_0=fill(1,sum(nint_u))` or *`sigmaPint_u_0`* : same than `σP_0` but for the unmeasured   disturbances at manipulated inputs $\mathbf{P_{int_u}}(0)$ (composed of integrators).
  * `σQint_ym=fill(1,sum(nint_ym))` or *`sigmaQint_u`* : same than `σQ` for the unmeasured   disturbances at measured outputs $\mathbf{Q_{int_{ym}}}$ (composed of integrators).
  * `σPint_ym_0=fill(1,sum(nint_ym))` or *`sigmaPint_ym_0`* : same than `σP_0` but for the unmeasured   disturbances at measured outputs $\mathbf{P_{int_{ym}}}(0)$ (composed of integrators).
  * `direct=true`: construct with a direct transmission from $\mathbf{y^m}$ (a.k.a. current  estimator, in opposition to the delayed/predictor form).

# Examples

```jldoctest
julia> model = LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 0.5);

julia> estim = KalmanFilter(model, i_ym=[2], σR=[1], σP_0=[100, 100], σQint_ym=[0.01])
KalmanFilter estimator with a sample time Ts = 0.5 s, LinModel and:
 1 manipulated inputs u (0 integrating states)
 3 estimated states x̂
 1 measured outputs ym (1 integrating states)
 1 unmeasured outputs yu
 0 measured disturbances d
```
