```
MovingHorizonEstimator(model::SimModel; <keyword arguments>)
```

Construct a moving horizon estimator (MHE) based on `model` ([`LinModel`](@ref) or [`NonLinModel`](@ref)).

It can handle constraints on the estimates, see [`setconstraint!`](@ref). Additionally,  `model` is not linearized like the [`ExtendedKalmanFilter`](@ref), and the probability  distribution is not approximated like the [`UnscentedKalmanFilter`](@ref). The computational costs are drastically higher, however, since it minimizes the following objective function at each discrete time $k$:

$$
\min_{\mathbf{x̂}_k(k-N_k+p), \mathbf{Ŵ}, ϵ}   \mathbf{x̄}' \mathbf{P̄}^{-1}       \mathbf{x̄} 
                                            + \mathbf{Ŵ}' \mathbf{Q̂}_{N_k}^{-1} \mathbf{Ŵ}  
                                            + \mathbf{V̂}' \mathbf{R̂}_{N_k}^{-1} \mathbf{V̂}
                                            + C ϵ^2
$$

in which the arrival costs are evaluated from the states estimated at time $k-N_k$:

$$
\begin{aligned}
    \mathbf{x̄} &= \mathbf{x̂}_{k-N_k}(k-N_k+p) - \mathbf{x̂}_k(k-N_k+p) \\
    \mathbf{P̄} &= \mathbf{P̂}_{k-N_k}(k-N_k+p)
\end{aligned}
$$

and the covariances are repeated $N_k$ times:

$$
\begin{aligned}
    \mathbf{Q̂}_{N_k} &= \text{diag}\mathbf{(Q̂,Q̂,...,Q̂)}  \\
    \mathbf{R̂}_{N_k} &= \text{diag}\mathbf{(R̂,R̂,...,R̂)} 
\end{aligned}
$$

The estimation horizon $H_e$ limits the window length:

$$
N_k =                     \begin{cases}
    k + 1   &  k < H_e    \\
    H_e     &  k ≥ H_e    \end{cases}
$$

The vectors $\mathbf{Ŵ}$ and $\mathbf{V̂}$ respectively encompass the estimated process noises $\mathbf{ŵ}(k-j+p)$ from $j=N_k$ to $1$ and sensor noises $\mathbf{v̂}(k-j+1)$ from $j=N_k$ to $1$. The Extended Help defines the two vectors, the slack variable $ϵ$, and the estimation of the covariance at arrival $\mathbf{P̂}_{k-N_k}(k-N_k+p)$. If the keyword argument `direct=true` (default value), the constant $p=0$ in the equations above, and the MHE is in the current form. Else $p=1$, leading to the prediction form.

See [`UnscentedKalmanFilter`](@ref) for details on the augmented process model and  $\mathbf{R̂}, \mathbf{Q̂}$ covariances. This estimator allocates a fair amount of memory  at each time step for the optimization, which is hard-coded as a single shooting transcription for now.

!!! warning
    See the Extended Help if you get an error like:     `MethodError: no method matching (::var"##")(::Vector{ForwardDiff.Dual})`.


# Arguments

!!! info
    Keyword arguments with *`emphasis`* are non-Unicode alternatives.


  * `model::SimModel` : (deterministic) model for the estimations.
  * `He=nothing` : estimation horizon $H_e$, must be specified.
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
  * `Cwt=Inf` : slack variable weight $C$, default to `Inf` meaning hard constraints only.
  * `optim=default_optim_mhe(model)` : a [`JuMP.Model`](@extref) object with a quadratic or  nonlinear optimizer for solving (default to [`Ipopt`](https://github.com/jump-dev/Ipopt.jl),  or [`OSQP`](https://osqp.org/docs/parsers/jump.html) if `model` is a [`LinModel`](@ref)).
  * `gradient=AutoForwardDiff()` : an `AbstractADType` backend for the gradient of the objective  function when `model` is not a [`LinModel`](@ref), see [`DifferentiationInterface` doc](@extref DifferentiationInterface List).
  * `jacobian=AutoForwardDiff()` : an `AbstractADType` backend for the Jacobian of the  constraints when `model` is not a [`LinModel`](@ref), see `gradient` above for the options.
  * `direct=true`: construct with a direct transmission from $\mathbf{y^m}$ (a.k.a. current  estimator, in opposition to the delayed/predictor form).

# Examples

```jldoctest
julia> model = NonLinModel((x,u,_,_)->0.1x+u, (x,_,_)->2x, 10.0, 1, 1, 1, solver=nothing);

julia> estim = MovingHorizonEstimator(model, He=5, σR=[1], σP_0=[0.01])
MovingHorizonEstimator estimator with a sample time Ts = 10.0 s, Ipopt optimizer, NonLinModel and:
 5 estimation steps He
 0 slack variable ϵ (estimation constraints)
 1 manipulated inputs u (0 integrating states)
 2 estimated states x̂
 1 measured outputs ym (1 integrating states)
 0 unmeasured outputs yu
 0 measured disturbances d
```

# Extended Help

!!! details "Extended Help"
    The estimated process and sensor noises are defined as:

    $$
    \mathbf{Ŵ} = 
    \begin{bmatrix}
        \mathbf{ŵ}(k-N_k+p+0)     \\
        \mathbf{ŵ}(k-N_k+p+1)     \\
        \vdots                  \\
        \mathbf{ŵ}(k+p-1)
    \end{bmatrix} , \quad
    \mathbf{V̂} =
    \begin{bmatrix}
        \mathbf{v̂}(k-N_k+1)     \\
        \mathbf{v̂}(k-N_k+2)     \\
        \vdots                  \\
        \mathbf{v̂}(k)
    \end{bmatrix}
    $$

    based on the augmented model functions $\mathbf{f̂, ĥ^m}$:

    $$
    \begin{aligned}
        \mathbf{v̂}(k-j)     &= \mathbf{y^m}(k-j) - \mathbf{ĥ^m}\Big(\mathbf{x̂}_k(k-j), \mathbf{d}(k-j)\Big) \\
        \mathbf{x̂}_k(k-j+1) &= \mathbf{f̂}\Big(\mathbf{x̂}_k(k-j), \mathbf{u}(k-j), \mathbf{d}(k-j)\Big) + \mathbf{ŵ}(k-j)
    \end{aligned}
    $$

    The constant $p$ equals to `!direct`. In other words, $\mathbf{Ŵ}$ and $\mathbf{V̂}$ are shifted by one time step if `direct==true`. The non-default prediction form with $p=1$ is particularly useful for the MHE since it moves its expensive computations after the MPC optimization. That is, [`preparestate!`](@ref) will solve the optimization by default, but it can be postponed to [`updatestate!`](@ref) with `direct=false`.

    The Extended Help of [`SteadyKalmanFilter`](@ref) details the tuning of the covariances and the augmentation with `nint_ym` and `nint_u` arguments. The default augmentation scheme is identical, that is `nint_u=0` and `nint_ym` computed by [`default_nint`](@ref). Note that the constructor does not validate the observability of the resulting augmented [`NonLinModel`](@ref). In such cases, it is the user's responsibility to ensure that it is still observable.

    The estimation covariance at arrival $\mathbf{P̂}_{k-N_k}(k-N_k+p)$ gives an uncertainty on the state estimate at the beginning of the window $k-N_k+p$, that is, in the past. It is not the same as the current estimate covariance $\mathbf{P̂}_k(k)$, a value not computed by the MHE (contrarily to e.g. the [`KalmanFilter`](@ref)). Three keyword arguments specify its initial value with $\mathbf{P̂_i} =  \mathrm{diag}\{ \mathbf{P}(0), \mathbf{P_{int_{u}}}(0), \mathbf{P_{int_{ym}}}(0) \}$. The initial state estimate $\mathbf{x̂_i}$ can be manually specified with [`setstate!`](@ref), or automatically  with [`initstate!`](@ref) for [`LinModel`](@ref). Note the MHE with $p=0$ is slightly inconsistent with all the other estimators here. It interprets the initial values as $\mathbf{x̂_i} = \mathbf{x̂}_{-1}(-1)$ and  $\mathbf{P̂_i} = \mathbf{P̂}_{-1}(-1)$, an  *a posteriori* estimate[^2] from the last time step. The MHE with $p=1$ is consistent, interpreting them as  $\mathbf{x̂_i} = \mathbf{x̂}_{-1}(0)$ and $\mathbf{P̂_i} = \mathbf{P̂}_{-1}(0)$.

    [^2]: M. Hovd (2012), "A Note On The Smoothing Formulation Of Moving Horizon Estimation",   *Facta Universitatis*, Vol. 11 №2.

    The optimization and the update of the arrival covariance depend on `model`:

      * If `model` is a [`LinModel`](@ref), the optimization is treated as a quadratic program with a time-varying Hessian, which is generally cheaper than nonlinear programming. By default, a [`KalmanFilter`](@ref) estimates the arrival covariance (customizable).
      * Else, a nonlinear program with dense [`ForwardDiff`](@extref ForwardDiff) automatic differentiation (AD) compute the objective and constraint derivatives by default  (customizable). Optimizers generally benefit from exact derivatives like AD. However,  the `f` and `h` functions must be compatible with this feature. See the  [`JuMP` documentation](@extref JuMP Common-mistakes-when-writing-a-user-defined-operator) for common mistakes when writing these functions. Also, an [`UnscentedKalmanFilter`](@ref) estimates the arrival covariance by default.

    The slack variable $ϵ$ relaxes the constraints if enabled, see [`setconstraint!`](@ref).  It is disabled by default for the MHE (from `Cwt=Inf`) but it should be activated for problems with two or more types of bounds, to ensure feasibility (e.g. on the estimated state $\mathbf{x̂}$ and sensor noise $\mathbf{v̂}$). Note that if `Cwt≠Inf`, the attribute `nlp_scaling_max_gradient` of `Ipopt` is set to  `10/Cwt` (if not already set),  to scale the small values of $ϵ$. Use the second constructor to specify the arrival covariance estimation method.

