```
LinMPC(model::LinModel; <keyword arguments>)
```

Construct a linear predictive controller based on [`LinModel`](@ref) `model`.

The controller minimizes the following objective function at each discrete time $k$:

$$
\begin{aligned}
\min_{\mathbf{Z}, ϵ}    \mathbf{(R̂_y - Ŷ)}' \mathbf{M}_{H_p} \mathbf{(R̂_y - Ŷ)}
                      + \mathbf{(ΔU)}'      \mathbf{N}_{H_c} \mathbf{(ΔU)}        \\
                      + \mathbf{(R̂_u - U)}' \mathbf{L}_{H_p} \mathbf{(R̂_u - U)} 
                      + C ϵ^2
\end{aligned}
$$

subject to [`setconstraint!`](@ref) bounds, and in which the weight matrices are repeated  $H_p$ or $H_c$ times by default:

$$
\begin{aligned}
    \mathbf{M}_{H_p} &= \text{diag}\mathbf{(M,M,...,M)}     \\
    \mathbf{N}_{H_c} &= \text{diag}\mathbf{(N,N,...,N)}     \\
    \mathbf{L}_{H_p} &= \text{diag}\mathbf{(L,L,...,L)}     
\end{aligned}
$$

Time-varying and non-diagonal weights are also supported. Modify the last block in  $\mathbf{M}_{H_p}$ to specify a terminal weight. The content of the decision vector $\mathbf{Z}$ depends on the chosen [`TranscriptionMethod`](@ref) (default to [`SingleShooting`](@ref), hence $\mathbf{Z = ΔU}$). The $\mathbf{ΔU}$ includes the input increments $\mathbf{Δu}(k+j) = \mathbf{u}(k+j) - \mathbf{u}(k+j-1)$ from $j=0$ to $H_c-1$, the $\mathbf{Ŷ}$ vector, the output predictions $\mathbf{ŷ}(k+j)$ from $j=1$ to $H_p$, and the $\mathbf{U}$ vector, the manipulated inputs $\mathbf{u}(k+j)$ from $j=0$ to $H_p-1$. The slack variable $ϵ$ relaxes the constraints, as described in [`setconstraint!`](@ref) documentation. See Extended Help for a detailed nomenclature. 

This method uses the default state estimator, a [`SteadyKalmanFilter`](@ref) with default arguments. This controller allocates memory at each time step for the optimization.

# Arguments

  * `model::LinModel` : model used for controller predictions and state estimations.
  * `Hp=10+nk` : prediction horizon $H_p$, `nk` is the number of delays in `model`.
  * `Hc=2` : control horizon $H_c$.
  * `Mwt=fill(1.0,model.ny)` : main diagonal of $\mathbf{M}$ weight matrix (vector).
  * `Nwt=fill(0.1,model.nu)` : main diagonal of $\mathbf{N}$ weight matrix (vector).
  * `Lwt=fill(0.0,model.nu)` : main diagonal of $\mathbf{L}$ weight matrix (vector).
  * `M_Hp=Diagonal(repeat(Mwt,Hp))` : positive semidefinite symmetric matrix $\mathbf{M}_{H_p}$.
  * `N_Hc=Diagonal(repeat(Nwt,Hc))` : positive semidefinite symmetric matrix $\mathbf{N}_{H_c}$.
  * `L_Hp=Diagonal(repeat(Lwt,Hp))` : positive semidefinite symmetric matrix $\mathbf{L}_{H_p}$.
  * `Cwt=1e5` : slack variable weight $C$ (scalar), use `Cwt=Inf` for hard constraints only.
  * `transcription=SingleShooting()` : a [`TranscriptionMethod`](@ref) for the optimization.
  * `optim=JuMP.Model(OSQP.MathOptInterfaceOSQP.Optimizer)` : quadratic optimizer used in the predictive controller, provided as a [`JuMP.Model`](@extref) object (default to  [`OSQP`](https://osqp.org/docs/parsers/jump.html) optimizer).
  * additional keyword arguments are passed to [`SteadyKalmanFilter`](@ref) constructor.

# Examples

```jldoctest
julia> model = LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 4);

julia> mpc = LinMPC(model, Mwt=[0, 1], Nwt=[0.5], Hp=30, Hc=1)
LinMPC controller with a sample time Ts = 4.0 s, OSQP optimizer, SteadyKalmanFilter estimator and:
 30 prediction steps Hp
  1 control steps Hc
  1 slack variable ϵ (control constraints)
  1 manipulated inputs u (0 integrating states)
  4 estimated states x̂
  2 measured outputs ym (2 integrating states)
  0 unmeasured outputs yu
  0 measured disturbances d
```

# Extended Help

!!! details "Extended Help"
    Manipulated inputs setpoints $\mathbf{r_u}$ are not common but they can be interesting for over-actuated systems, when `nu > ny` (e.g. prioritize solutions with lower  economical costs). The default `Lwt` value implies that this feature is disabled by default.

    The objective function follows this nomenclature:

    | VARIABLE           | DESCRIPTION                                            | SIZE             |
    |:------------------ |:------------------------------------------------------ |:---------------- |
    | $H_p$              | prediction horizon (integer)                           | `()`             |
    | $H_c$              | control horizon (integer)                              | `()`             |
    | $\mathbf{Z}$       | decision variable vector (excluding $ϵ$)               | var.             |
    | $\mathbf{ΔU}$      | manipulated input increments over $H_c$                | `(nu*Hc,)`       |
    | $\mathbf{D̂}$      | predicted measured disturbances over $H_p$             | `(nd*Hp,)`       |
    | $\mathbf{Ŷ}$      | predicted outputs over $H_p$                           | `(ny*Hp,)`       |
    | $\mathbf{X̂}$      | predicted states over $H_p$                            | `(nx̂*Hp,)`      |
    | $\mathbf{U}$       | manipulated inputs over $H_p$                          | `(nu*Hp,)`       |
    | $\mathbf{R̂_y}$    | predicted output setpoints over $H_p$                  | `(ny*Hp,)`       |
    | $\mathbf{R̂_u}$    | predicted manipulated input setpoints over $H_p$       | `(nu*Hp,)`       |
    | $\mathbf{M}_{H_p}$ | output setpoint tracking weights over $H_p$            | `(ny*Hp, ny*Hp)` |
    | $\mathbf{N}_{H_c}$ | manipulated input increment weights over $H_c$         | `(nu*Hc, nu*Hc)` |
    | $\mathbf{L}_{H_p}$ | manipulated input setpoint tracking weights over $H_p$ | `(nu*Hp, nu*Hp)` |
    | $C$                | slack variable weight                                  | `()`             |
    | $ϵ$                | slack variable for constraint softening                | `()`             |

