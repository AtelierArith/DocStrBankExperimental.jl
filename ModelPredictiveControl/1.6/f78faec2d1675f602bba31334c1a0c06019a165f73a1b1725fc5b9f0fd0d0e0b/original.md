```
ExtendedKalmanFilter(model::SimModel; <keyword arguments>)
```

Construct an extended Kalman Filter with the [`SimModel`](@ref) `model`.

Both [`LinModel`](@ref) and [`NonLinModel`](@ref) are supported. The process model is identical to [`UnscentedKalmanFilter`](@ref). By default, the Jacobians of the augmented model $\mathbf{f̂, ĥ}$ are computed with [`ForwardDiff`](@extref ForwardDiff) automatic differentiation. This estimator is allocation-free if `model` simulations do not allocate.

!!! warning
    See the Extended Help of [`linearize`](@ref) function if you get an error like:     `MethodError: no method matching (::var"##")(::Vector{ForwardDiff.Dual})`.


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
  * `jacobian=AutoForwardDiff()`: an `AbstractADType` backend for the Jacobians of the augmented   model, see [`DifferentiationInterface` doc](@extref DifferentiationInterface List).
  * `direct=true`: construct with a direct transmission from $\mathbf{y^m}$ (a.k.a. current  estimator, in opposition to the delayed/predictor form).

# Examples

```jldoctest
julia> model = NonLinModel((x,u,_,_)->0.2x+u, (x,_,_)->-3x, 5.0, 1, 1, 1, solver=nothing);

julia> estim = ExtendedKalmanFilter(model, σQ=[2], σQint_ym=[2], σP_0=[0.1], σPint_ym_0=[0.1])
ExtendedKalmanFilter estimator with a sample time Ts = 5.0 s, NonLinModel and:
 1 manipulated inputs u (0 integrating states)
 2 estimated states x̂
 1 measured outputs ym (1 integrating states)
 0 unmeasured outputs yu
 0 measured disturbances d
```
