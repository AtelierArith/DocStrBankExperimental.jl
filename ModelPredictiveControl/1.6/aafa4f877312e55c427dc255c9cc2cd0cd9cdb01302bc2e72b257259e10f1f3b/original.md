```
setconstraint!(mpc::PredictiveController; <keyword arguments>) -> mpc
```

Set the bound constraint parameters of the [`PredictiveController`](@ref) `mpc`.

The predictive controllers support both soft and hard constraints, defined by:

$$
\begin{alignat*}{3}
    \mathbf{u_{min}  - c_{u_{min}}}  ϵ ≤&&\       \mathbf{u}(k+j) &≤ \mathbf{u_{max}  + c_{u_{max}}}  ϵ &&\qquad  j = 0, 1 ,..., H_p - 1 \\
    \mathbf{Δu_{min} - c_{Δu_{min}}} ϵ ≤&&\      \mathbf{Δu}(k+j) &≤ \mathbf{Δu_{max} + c_{Δu_{max}}} ϵ &&\qquad  j = 0, 1 ,..., H_c - 1 \\
    \mathbf{y_{min}  - c_{y_{min}}}  ϵ ≤&&\       \mathbf{ŷ}(k+j) &≤ \mathbf{y_{max}  + c_{y_{max}}}  ϵ &&\qquad  j = 1, 2 ,..., H_p     \\
    \mathbf{x̂_{min}  - c_{x̂_{min}}}  ϵ ≤&&\     \mathbf{x̂}_i(k+j) &≤ \mathbf{x̂_{max}  + c_{x̂_{max}}}  ϵ &&\qquad  j = H_p
\end{alignat*}
$$

and also $ϵ ≥ 0$. The last line is the terminal constraints applied on the states at the end of the horizon (see Extended Help). See [`MovingHorizonEstimator`](@ref) constraints for details on bounds and softness parameters $\mathbf{c}$. The output and terminal  constraints are all soft by default. See Extended Help for time-varying constraints.

# Arguments

!!! info
    The keyword arguments `Δumin`, `Δumax`, `c_Δumin`, `c_Δumax`, `x̂min`, `x̂max`, `c_x̂min`, `c_x̂max` and their capital letter versions have non-Unicode alternatives e.g.  *`Deltaumin`*, *`xhatmax`* and *`C_Deltaumin`*

    The default constraints are mentioned here for clarity but omitting a keyword argument  will not re-assign to its default value (defaults are set at construction only).


  * `mpc::PredictiveController` : predictive controller to set constraints
  * `umin=fill(-Inf,nu)` / `umax=fill(+Inf,nu)` : manipulated input bound $\mathbf{u_{min/max}}$
  * `Δumin=fill(-Inf,nu)` / `Δumax=fill(+Inf,nu)` : manipulated input increment bound $\mathbf{Δu_{min/max}}$
  * `ymin=fill(-Inf,ny)` / `ymax=fill(+Inf,ny)` : predicted output bound $\mathbf{y_{min/max}}$
  * `x̂min=fill(-Inf,nx̂)` / `x̂max=fill(+Inf,nx̂)` : terminal constraint bound $\mathbf{x̂_{min/max}}$
  * `c_umin=fill(0.0,nu)` / `c_umax=fill(0.0,nu)` : `umin` / `umax` softness weight $\mathbf{c_{u_{min/max}}}$
  * `c_Δumin=fill(0.0,nu)` / `c_Δumax=fill(0.0,nu)` : `Δumin` / `Δumax` softness weight $\mathbf{c_{Δu_{min/max}}}$
  * `c_ymin=fill(1.0,ny)` / `c_ymax=fill(1.0,ny)` : `ymin` / `ymax` softness weight $\mathbf{c_{y_{min/max}}}$
  * `c_x̂min=fill(1.0,nx̂)` / `c_x̂max=fill(1.0,nx̂)` : `x̂min` / `x̂max` softness weight $\mathbf{c_{x̂_{min/max}}}$
  * all the keyword arguments above but with a first capital letter, except for the terminal constraints, e.g. `Ymax` or `C_Δumin`: for time-varying constraints (see Extended Help)

# Examples

```jldoctest
julia> mpc = LinMPC(setop!(LinModel(tf(3, [30, 1]), 4), uop=[50], yop=[25]));

julia> mpc = setconstraint!(mpc, umin=[0], umax=[100], Δumin=[-10], Δumax=[+10])
LinMPC controller with a sample time Ts = 4.0 s, OSQP optimizer, SteadyKalmanFilter estimator and:
 10 prediction steps Hp
  2 control steps Hc
  1 slack variable ϵ (control constraints)
  1 manipulated inputs u (0 integrating states)
  2 estimated states x̂
  1 measured outputs ym (1 integrating states)
  0 unmeasured outputs yu
  0 measured disturbances d
```

# Extended Help

!!! details "Extended Help"
    Terminal constraints provide closed-loop stability guarantees on the nominal plant model. They can render an unfeasible problem however. In practice, a sufficiently large prediction horizon $H_p$ without terminal constraints is typically enough for  stability. If `mpc.estim.direct==true`, the estimator computes the states at $i = k$  (the current time step), otherwise at $i = k - 1$. Note that terminal constraints are applied on the augmented state vector $\mathbf{x̂}$ (see [`SteadyKalmanFilter`](@ref) for details on augmentation).

    For variable constraints, the bounds can be modified after calling [`moveinput!`](@ref), that is, at runtime, but not the softness parameters $\mathbf{c}$. It is not possible to modify `±Inf` bounds at runtime.

    !!! tip
        To keep a variable unconstrained while maintaining the ability to add a constraint later at runtime, set the bound to an absolute value sufficiently large when you create the controller (but different than `±Inf`).


    It is also possible to specify time-varying constraints over $H_p$ and $H_c$  horizons. In such a case, they are defined by:

    $$
    \begin{alignat*}{3}
        \mathbf{U_{min}  - C_{u_{min}}}  ϵ ≤&&\ \mathbf{U}  &≤ \mathbf{U_{max}  + C_{u_{max}}}  ϵ \\
        \mathbf{ΔU_{min} - C_{Δu_{min}}} ϵ ≤&&\ \mathbf{ΔU} &≤ \mathbf{ΔU_{max} + C_{Δu_{max}}} ϵ \\
        \mathbf{Y_{min}  - C_{y_{min}}}  ϵ ≤&&\ \mathbf{Ŷ}  &≤ \mathbf{Y_{max}  + C_{y_{max}}}  ϵ
    \end{alignat*}
    $$

    For this, use the same keyword arguments as above but with a first capital letter:

      * `Umin`  / `Umax`  / `C_umin`  / `C_umax`  : $\mathbf{U}$ constraints `(nu*Hp,)`.
      * `ΔUmin` / `ΔUmax` / `C_Δumin` / `C_Δumax` : $\mathbf{ΔU}$ constraints `(nu*Hc,)`.
      * `Ymin`  / `Ymax`  / `C_ymin`  / `C_ymax`  : $\mathbf{Ŷ}$ constraints `(ny*Hp,)`.

