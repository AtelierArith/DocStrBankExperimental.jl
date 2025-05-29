```
UnscentedKalmanFilter(model::SimModel; <keyword arguments>)
```

Construct an unscented Kalman Filter with the [`SimModel`](@ref) `model`.

Both [`LinModel`](@ref) and [`NonLinModel`](@ref) are supported. The unscented Kalman filter is based on the process model :

$$
\begin{aligned}
    \mathbf{x}(k+1) &= \mathbf{f̂}\Big(\mathbf{x}(k), \mathbf{u}(k), \mathbf{d}(k)\Big) 
                        + \mathbf{w}(k)                                                   \\
    \mathbf{y^m}(k) &= \mathbf{ĥ^m}\Big(\mathbf{x}(k), \mathbf{d}(k)\Big) + \mathbf{v}(k) \\
    \mathbf{y^u}(k) &= \mathbf{ĥ^u}\Big(\mathbf{x}(k), \mathbf{d}(k)\Big)                 \\
\end{aligned}
$$

See [`SteadyKalmanFilter`](@ref) for details on $\mathbf{v}(k), \mathbf{w}(k)$ noises and $\mathbf{R̂}, \mathbf{Q̂}$ covariances. The two matrices are constructed from $\mathbf{Q̂ = \text{diag}(Q, Q_{int_u}, Q_{int_{ym}})}$ and $\mathbf{R̂ = R}$. The functions $\mathbf{f̂, ĥ}$ are `model` state-space functions augmented with the stochastic model of the unmeasured disturbances, which is specified by the numbers of integrator `nint_u` and `nint_ym` (see Extended Help). Model parameters $\mathbf{p}$ are not argument of $\mathbf{f̂, ĥ}$ functions for conciseness. The $\mathbf{ĥ^m}$ function represents the measured outputs of $\mathbf{ĥ}$ function (and unmeasured ones, for $\mathbf{ĥ^u}$). The matrix $\mathbf{P̂}$ is the estimation error covariance of `model` state augmented with the  stochastic ones. Three keyword arguments specify its initial value with $\mathbf{P̂}_{-1}(0) =  \mathrm{diag}\{ \mathbf{P}(0), \mathbf{P_{int_{u}}}(0), \mathbf{P_{int_{ym}}}(0) \}$. The  initial state estimate $\mathbf{x̂}_{-1}(0)$ can be manually specified with [`setstate!`](@ref). This estimator is allocation-free if `model` simulations do not allocate.

# Arguments

!!! info
    Keyword arguments with *`emphasis`* are non-Unicode alternatives.


  * `model::SimModel` : (deterministic) model for the estimations.
  * `i_ym=1:model.ny` : `model` output indices that are measured $\mathbf{y^m}$, the rest    are unmeasured $\mathbf{y^u}$.
  * `σP_0=fill(1/model.nx,model.nx)` or *`sigmaP_0`* : main diagonal of the initial estimate   covariance $\mathbf{P}(0)$, specified as a standard deviation vector.
  * `σQ=fill(1/model.nx,model.nx)` or *`sigmaQ`* : main diagonal of the process noise   covariance $\mathbf{Q}$ of `model`, specified as a standard deviation vector.
  * `σR=fill(1,length(i_ym))` or *`sigmaR`* : main diagonal of the sensor noise covariance   $\mathbf{R}$ of `model` measured outputs, specified as a standard deviation vector.
  * `nint_u=0`: integrator quantity for the stochastic model of the unmeasured disturbances at   the manipulated inputs (vector), use `nint_u=0` for no integrator (see Extended Help).
  * `nint_ym=default_nint(model,i_ym,nint_u)` : same than `nint_u` but for the unmeasured    disturbances at the measured outputs, use `nint_ym=0` for no integrator (see Extended Help).
  * `σQint_u=fill(1,sum(nint_u))` or *`sigmaQint_u`* : same than `σQ` but for the unmeasured   disturbances at manipulated inputs $\mathbf{Q_{int_u}}$ (composed of integrators).
  * `σPint_u_0=fill(1,sum(nint_u))` or *`sigmaPint_u_0`* : same than `σP_0` but for the unmeasured   disturbances at manipulated inputs $\mathbf{P_{int_u}}(0)$ (composed of integrators).
  * `σQint_ym=fill(1,sum(nint_ym))` or *`sigmaQint_u`* : same than `σQ` for the unmeasured   disturbances at measured outputs $\mathbf{Q_{int_{ym}}}$ (composed of integrators).
  * `σPint_ym_0=fill(1,sum(nint_ym))` or *`sigmaPint_ym_0`* : same than `σP_0` but for the unmeasured   disturbances at measured outputs $\mathbf{P_{int_{ym}}}(0)$ (composed of integrators).
  * `α=1e-3` or *`alpha`* : alpha parameter, spread of the state distribution $(0 < α ≤ 1)$.
  * `β=2` or *`beta`* : beta parameter, skewness and kurtosis of the states distribution $(β ≥ 0)$.
  * `κ=0` or *`kappa`* : kappa parameter, another spread parameter $(0 ≤ κ ≤ 3)$.
  * `direct=true`: construct with a direct transmission from $\mathbf{y^m}$ (a.k.a. current  estimator, in opposition to the delayed/predictor form).

# Examples

```jldoctest
julia> model = NonLinModel((x,u,_,_)->0.1x+u, (x,_,_)->2x, 10.0, 1, 1, 1, solver=nothing);

julia> estim = UnscentedKalmanFilter(model, σR=[1], nint_ym=[2], σPint_ym_0=[1, 1])
UnscentedKalmanFilter estimator with a sample time Ts = 10.0 s, NonLinModel and:
 1 manipulated inputs u (0 integrating states)
 3 estimated states x̂
 1 measured outputs ym (2 integrating states)
 0 unmeasured outputs yu
 0 measured disturbances d
```

# Extended Help

!!! details "Extended Help"
    The Extended Help of [`SteadyKalmanFilter`](@ref) details the tuning of the covariances and the augmentation with `nint_ym` and `nint_u` arguments. The default augmentation scheme is identical, that is `nint_u=0` and `nint_ym` computed by [`default_nint`](@ref). Note that the constructor does not validate the observability of the resulting augmented [`NonLinModel`](@ref). In such cases, it is the user's responsibility to ensure that it is still observable.

