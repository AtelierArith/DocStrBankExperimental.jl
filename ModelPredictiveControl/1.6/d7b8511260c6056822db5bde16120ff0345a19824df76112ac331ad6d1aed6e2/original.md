```
setconstraint!(estim::MovingHorizonEstimator; <keyword arguments>) -> estim
```

Set the bound constraint parameters of the [`MovingHorizonEstimator`](@ref) `estim`.

It supports both soft and hard constraints on the estimated state $\mathbf{x̂}$, process  noise $\mathbf{ŵ}$ and sensor noise $\mathbf{v̂}$:

$$
\begin{alignat*}{3}
    \mathbf{x̂_{min} - c_{x̂_{min}}} ϵ ≤&&\   \mathbf{x̂}_k(k-j+p) &≤ \mathbf{x̂_{max} + c_{x̂_{max}}} ϵ &&\qquad  j = N_k, N_k - 1, ... , 0    \\
    \mathbf{ŵ_{min} - c_{ŵ_{min}}} ϵ ≤&&\     \mathbf{ŵ}(k-j+p) &≤ \mathbf{ŵ_{max} + c_{ŵ_{max}}} ϵ &&\qquad  j = N_k, N_k - 1, ... , 1    \\
    \mathbf{v̂_{min} - c_{v̂_{min}}} ϵ ≤&&\     \mathbf{v̂}(k-j+1) &≤ \mathbf{v̂_{max} + c_{v̂_{max}}} ϵ &&\qquad  j = N_k, N_k - 1, ... , 1
\end{alignat*}
$$

and also $ϵ ≥ 0$. All the constraint parameters are vector. Use `±Inf` values when there is no bound. The constraint softness parameters $\mathbf{c}$, also called equal concern for relaxation, are non-negative values that specify the softness of the associated bound. Use `0.0` values for hard constraints (default for all of them). Notice that constraining the estimated sensor noises is equivalent to bounding the innovation term, since  $\mathbf{v̂}(k) = \mathbf{y^m}(k) - \mathbf{ŷ^m}(k)$. See Extended Help for details on the constant $p$, on model augmentation and on time-varying constraints.

# Arguments

!!! info
    All the keyword arguments have non-Unicode alternatives e.g. *`xhatmin`* or *`Vhatmax`*. 

    The default constraints are mentioned here for clarity but omitting a keyword argument  will not re-assign to its default value (defaults are set at construction only).


  * `estim::MovingHorizonEstimator` : moving horizon estimator to set constraints
  * `x̂min=fill(-Inf,nx̂)` / `x̂max=fill(+Inf,nx̂)` : estimated state bound $\mathbf{x̂_{min/max}}$
  * `ŵmin=fill(-Inf,nx̂)` / `ŵmax=fill(+Inf,nx̂)` : estimated process noise bound $\mathbf{ŵ_{min/max}}$
  * `v̂min=fill(-Inf,nym)` / `v̂max=fill(+Inf,nym)` : estimated sensor noise bound $\mathbf{v̂_{min/max}}$
  * `c_x̂min=fill(0.0,nx̂)` / `c_x̂max=fill(0.0,nx̂)` : `x̂min` / `x̂max` softness weight $\mathbf{c_{x̂_{min/max}}}$
  * `c_ŵmin=fill(0.0,nx̂)` / `c_ŵmax=fill(0.0,nx̂)` : `ŵmin` / `ŵmax` softness weight $\mathbf{c_{ŵ_{min/max}}}$
  * `c_v̂min=fill(0.0,nym)` / `c_v̂max=fill(0.0,nym)` : `v̂min` / `v̂max` softness weight $\mathbf{c_{v̂_{min/max}}}$
  * all the keyword arguments above but with a first capital letter, e.g. `X̂max` or `C_ŵmax`:  for time-varying constraints (see Extended Help)

# Examples

```jldoctest
julia> estim = MovingHorizonEstimator(LinModel(ss(0.5,1,1,0,1)), He=3);

julia> estim = setconstraint!(estim, x̂min=[-50, -50], x̂max=[50, 50])
MovingHorizonEstimator estimator with a sample time Ts = 1.0 s, OSQP optimizer, LinModel and:
 3 estimation steps He
 0 slack variable ϵ (estimation constraints)
 1 manipulated inputs u (0 integrating states)
 2 estimated states x̂
 1 measured outputs ym (1 integrating states)
 0 unmeasured outputs yu
 0 measured disturbances d
```

# Extended Help

!!! details "Extended Help"
    The constant $p=0$ if `estim.direct==true` (current form), else $p=1$ (prediction form). Note that the state $\mathbf{x̂}$ and process noise $\mathbf{ŵ}$ constraints are applied on the augmented model, detailed in [`SteadyKalmanFilter`](@ref) Extended Help. For variable constraints, the bounds can be modified after calling [`updatestate!`](@ref), that is, at runtime, except for `±Inf` bounds. Time-varying constraints over the estimation horizon $H_e$ are also possible, mathematically defined as:

    $$
    \begin{alignat*}{3}
        \mathbf{X̂_{min} - C_{x̂_{min}}} ϵ ≤&&\ \mathbf{X̂} &≤ \mathbf{X̂_{max} + C_{x̂_{max}}} ϵ \\
        \mathbf{Ŵ_{min} - C_{ŵ_{min}}} ϵ ≤&&\ \mathbf{Ŵ} &≤ \mathbf{Ŵ_{max} + C_{ŵ_{max}}} ϵ \\
        \mathbf{V̂_{min} - C_{v̂_{min}}} ϵ ≤&&\ \mathbf{V̂} &≤ \mathbf{V̂_{max} + C_{v̂_{max}}} ϵ
    \end{alignat*}
    $$

    For this, use the same keyword arguments as above but with a first capital letter:

      * `X̂min` / `X̂max` / `C_x̂min` / `C_x̂max` : $\mathbf{X̂}$ constraints `(nx̂*(He+1),)`.
      * `Ŵmin` / `Ŵmax` / `C_ŵmin` / `C_ŵmax` : $\mathbf{Ŵ}$ constraints `(nx̂*He,)`.
      * `V̂min` / `V̂max` / `C_v̂min` / `C_v̂max` : $\mathbf{V̂}$ constraints `(nym*He,)`.

