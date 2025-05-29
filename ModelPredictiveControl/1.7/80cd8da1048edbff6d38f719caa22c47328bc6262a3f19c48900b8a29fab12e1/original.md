```
SteadyKalmanFilter(model::LinModel; <keyword arguments>)
```

Construct a steady-state Kalman Filter with the [`LinModel`](@ref) `model`.

The steady-state (or [asymptotic](https://en.wikipedia.org/wiki/Kalman_filter#Asymptotic_form)) Kalman filter is based on the process model:

$$
\begin{aligned}
    \mathbf{x}(k+1) &= 
            \mathbf{Â x}(k) + \mathbf{B̂_u u}(k) + \mathbf{B̂_d d}(k) + \mathbf{w}(k) \\
    \mathbf{y^m}(k) &= \mathbf{Ĉ^m x}(k) + \mathbf{D̂_d^m d}(k) + \mathbf{v}(k) \\
    \mathbf{y^u}(k) &= \mathbf{Ĉ^u x}(k) + \mathbf{D̂_d^u d}(k)
\end{aligned}
$$

with sensor $\mathbf{v}(k)$ and process $\mathbf{w}(k)$ noises as uncorrelated zero mean  white noise vectors, with a respective covariance of $\mathbf{R̂}$ and $\mathbf{Q̂}$.  The arguments are in standard deviations σ, i.e. same units than outputs and states. The  matrices $\mathbf{Â, B̂_u, B̂_d, Ĉ, D̂_d}$ are `model` matrices augmented with the stochastic model, which is specified by the numbers of integrator `nint_u` and `nint_ym` (see Extended Help). Likewise, the covariance matrices are augmented with $\mathbf{Q̂ = \text{diag}(Q,  Q_{int_u}, Q_{int_{ym}})}$ and $\mathbf{R̂ = R}$. The Extended Help provide some guidelines on the covariance tuning. The matrices $\mathbf{Ĉ^m, D̂_d^m}$ are the rows of  $\mathbf{Ĉ, D̂_d}$ that correspond to measured outputs $\mathbf{y^m}$ (and unmeasured ones, for $\mathbf{Ĉ^u, D̂_d^u}$). The Kalman filter will estimate the current state with  the newest measurements $\mathbf{x̂}_k(k)$ if `direct` is `true`, else it will predict the state of the next time step $\mathbf{x̂}_k(k+1)$. This estimator is allocation-free.

# Arguments

!!! info
    Keyword arguments with *`emphasis`* are non-Unicode alternatives.


  * `model::LinModel` : (deterministic) model for the estimations.
  * `i_ym=1:model.ny` : `model` output indices that are measured $\mathbf{y^m}$, the rest    are unmeasured $\mathbf{y^u}$.
  * `σQ=fill(1/model.nx,model.nx)` or *`sigmaQ`* : main diagonal of the process noise   covariance $\mathbf{Q}$ of `model`, specified as a standard deviation vector.
  * `σR=fill(1,length(i_ym))` or *`sigmaR`* : main diagonal of the sensor noise covariance   $\mathbf{R}$ of `model` measured outputs, specified as a standard deviation vector.
  * `nint_u=0`: integrator quantity for the stochastic model of the unmeasured disturbances at   the manipulated inputs (vector), use `nint_u=0` for no integrator (see Extended Help).
  * `nint_ym=default_nint(model,i_ym,nint_u)` : same than `nint_u` but for the unmeasured    disturbances at the measured outputs, use `nint_ym=0` for no integrator (see Extended Help).
  * `σQint_u=fill(1,sum(nint_u))` or *`sigmaQint_u`* : same than `σQ` but for the unmeasured   disturbances at manipulated inputs $\mathbf{Q_{int_u}}$ (composed of integrators).
  * `σQint_ym=fill(1,sum(nint_ym))` or *`sigmaQint_u`* : same than `σQ` for the unmeasured   disturbances at measured outputs $\mathbf{Q_{int_{ym}}}$ (composed of integrators).
  * `direct=true`: construct with a direct transmission from $\mathbf{y^m}$ (a.k.a. current  estimator, in opposition to the delayed/predictor form).

# Examples

```jldoctest
julia> model = LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 0.5);

julia> estim = SteadyKalmanFilter(model, i_ym=[2], σR=[1], σQint_ym=[0.01])
SteadyKalmanFilter estimator with a sample time Ts = 0.5 s, LinModel and:
 1 manipulated inputs u (0 integrating states)
 3 estimated states x̂
 1 measured outputs ym (1 integrating states)
 1 unmeasured outputs yu
 0 measured disturbances d
```

# Extended Help

!!! details "Extended Help"
    The `σR` argument is generally fixed at the estimated standard deviations of the sensor noises. The `σQ`, `σQint_u` and `σQint_ym` arguments can be used to tune the filter response. Increasing them make the filter more responsive to disturbances but more sensitive to measurement noise.

    The model augmentation with `nint_u` vector adds integrators at model manipulated inputs, and `nint_ym`, at measured outputs. They create the integral action when the estimator is used in a controller as state feedback. By default, the method [`default_nint`](@ref) adds one integrator per measured output if feasible. The argument `nint_ym` can also be tweaked by following these rules on each measured output:

      * Use 0 integrator if the model output is already integrating (else it will be unobservable)
      * Use 1 integrator if the disturbances on the output are typically "step-like"
      * Use 2 integrators if the disturbances on the output are typically "ramp-like"

    The function [`init_estimstoch`](@ref) builds the stochastic model for estimation.

    !!! tip
        Increasing `σQint_u` and `σQint_ym` values increases the integral action "gain".


    The constructor pre-compute the steady-state Kalman gain `K̂` with the [`kalman`](@extref ControlSystemsBase.kalman) function. It can sometimes fail, for example when `model` matrices are ill-conditioned. In such a case, you can try the alternative time-varying [`KalmanFilter`](@ref).

