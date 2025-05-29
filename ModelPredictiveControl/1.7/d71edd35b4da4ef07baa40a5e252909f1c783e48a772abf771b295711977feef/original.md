```
NonLinMPC(model::SimModel; <keyword arguments>)
```

Construct a nonlinear predictive controller based on [`SimModel`](@ref) `model`.

Both [`NonLinModel`](@ref) and [`LinModel`](@ref) are supported (see Extended Help). The  controller minimizes the following objective function at each discrete time $k$:

$$
\begin{aligned}
\min_{\mathbf{Z}, ϵ}\ &  \mathbf{(R̂_y - Ŷ)}' \mathbf{M}_{H_p} \mathbf{(R̂_y - Ŷ)}   
                       + \mathbf{(ΔU)}'      \mathbf{N}_{H_c} \mathbf{(ΔU)}        \\&
                       + \mathbf{(R̂_u - U)}' \mathbf{L}_{H_p} \mathbf{(R̂_u - U)} 
                       + C ϵ^2  
                       + E J_E(\mathbf{U_e}, \mathbf{Ŷ_e}, \mathbf{D̂_e}, \mathbf{p})
\end{aligned}
$$

subject to [`setconstraint!`](@ref) bounds, and the custom inequality constraints:

$$
\mathbf{g_c}(\mathbf{U_e}, \mathbf{Ŷ_e}, \mathbf{D̂_e}, \mathbf{p}, ϵ) ≤ \mathbf{0}
$$

with the decision variables $\mathbf{Z}$ and slack $ϵ$. By default, a [`SingleShooting`](@ref) transcription method is used, hence $\mathbf{Z=ΔU}$. The economic function $J_E$ can penalizes solutions with high economic costs. Setting all the weights to 0 except $E$ creates a pure economic model predictive controller (EMPC). As a matter of fact, $J_E$ can be any nonlinear function as a custom objective, even if there is no economic interpretation to it. The arguments of $J_E$ and $\mathbf{g_c}$ include the manipulated inputs, predicted outputs and measured disturbances, extended from $k$ to $k+H_p$ (inclusively, see Extended Help for more details):

$$
    \mathbf{U_e} = \begin{bmatrix} \mathbf{U}      \\ \mathbf{u}(k+H_p-1)   \end{bmatrix}  , \quad
    \mathbf{Ŷ_e} = \begin{bmatrix} \mathbf{ŷ}(k)   \\ \mathbf{Ŷ}            \end{bmatrix}  , \quad
    \mathbf{D̂_e} = \begin{bmatrix} \mathbf{d}(k)   \\ \mathbf{D̂}            \end{bmatrix}
$$

The argument $\mathbf{p}$ is a custom parameter object of any type, but use a mutable one if you want to modify it later e.g.: a vector. See [`LinMPC`](@ref) Extended Help for the definition of the other variables.

!!! tip
    Replace any of the arguments of $J_E$ and $\mathbf{g_c}$ functions with `_` if not needed (see e.g. the default value of `JE` below).


This method uses the default state estimator:

  * if `model` is a [`LinModel`](@ref), a [`SteadyKalmanFilter`](@ref) with default arguments;
  * else, an [`UnscentedKalmanFilter`](@ref) with default arguments.

This controller allocates memory at each time step for the optimization.

!!! warning
    See Extended Help if you get an error like:     `MethodError: no method matching Float64(::ForwardDiff.Dual)`.


# Arguments

  * `model::SimModel` : model used for controller predictions and state estimations.
  * `Hp=nothing`: prediction horizon $H_p$, must be specified for [`NonLinModel`](@ref).
  * `Hc=2` : control horizon $H_c$.
  * `Mwt=fill(1.0,model.ny)` : main diagonal of $\mathbf{M}$ weight matrix (vector).
  * `Nwt=fill(0.1,model.nu)` : main diagonal of $\mathbf{N}$ weight matrix (vector).
  * `Lwt=fill(0.0,model.nu)` : main diagonal of $\mathbf{L}$ weight matrix (vector).
  * `M_Hp=Diagonal(repeat(Mwt,Hp))` : positive semidefinite symmetric matrix $\mathbf{M}_{H_p}$.
  * `N_Hc=Diagonal(repeat(Nwt,Hc))` : positive semidefinite symmetric matrix $\mathbf{N}_{H_c}$.
  * `L_Hp=Diagonal(repeat(Lwt,Hp))` : positive semidefinite symmetric matrix $\mathbf{L}_{H_p}$.
  * `Cwt=1e5` : slack variable weight $C$ (scalar), use `Cwt=Inf` for hard constraints only.
  * `Ewt=0.0` : economic costs weight $E$ (scalar).
  * `JE=(_,_,_,_)->0.0` : economic or custom cost function $J_E(\mathbf{U_e}, \mathbf{Ŷ_e},  \mathbf{D̂_e}, \mathbf{p})$.
  * `gc=(_,_,_,_,_,_)->nothing` or `gc!` : custom inequality constraint function   $\mathbf{g_c}(\mathbf{U_e}, \mathbf{Ŷ_e}, \mathbf{D̂_e}, \mathbf{p}, ϵ)$, mutating or   not (details in Extended Help).
  * `nc=0` : number of custom inequality constraints.
  * `p=model.p` : $J_E$ and $\mathbf{g_c}$ functions parameter $\mathbf{p}$ (any type).
  * `transcription=SingleShooting()` : a [`TranscriptionMethod`](@ref) for the optimization.
  * `optim=JuMP.Model(Ipopt.Optimizer)` : nonlinear optimizer used in the predictive  controller, provided as a [`JuMP.Model`](@extref) object (default to [`Ipopt`](https://github.com/jump-dev/Ipopt.jl) optimizer).
  * `gradient=AutoForwardDiff()` : an `AbstractADType` backend for the gradient of the objective  function, see [`DifferentiationInterface` doc](@extref DifferentiationInterface List).
  * `jacobian=default_jacobian(transcription)` : an `AbstractADType` backend for the Jacobian  of the nonlinear constraints, see `gradient` above for the options (default in Extended Help).
  * additional keyword arguments are passed to [`UnscentedKalmanFilter`](@ref) constructor  (or [`SteadyKalmanFilter`](@ref), for [`LinModel`](@ref)).

# Examples

```jldoctest
julia> model = NonLinModel((x,u,_,_)->0.5x+u, (x,_,_)->2x, 10.0, 1, 1, 1, solver=nothing);

julia> mpc = NonLinMPC(model, Hp=20, Hc=1, Cwt=1e6)
NonLinMPC controller with a sample time Ts = 10.0 s, Ipopt optimizer, UnscentedKalmanFilter estimator and:
 20 prediction steps Hp
  1 control steps Hc
  1 slack variable ϵ (control constraints)
  1 manipulated inputs u (0 integrating states)
  2 estimated states x̂
  1 measured outputs ym (1 integrating states)
  0 unmeasured outputs yu
  0 measured disturbances d
```

# Extended Help

!!! details "Extended Help"
    `NonLinMPC` controllers based on [`LinModel`](@ref) compute the predictions with matrix  algebra instead of a `for` loop. This feature can accelerate the optimization, especially for the constraint handling, and is not available in any other package, to my knowledge.

    The economic cost $J_E$ and custom constraint $\mathbf{g_c}$ functions receive the extended vectors $\mathbf{U_e}$ (`nu*Hp+nu` elements), $\mathbf{Ŷ_e}$ (`ny+ny*Hp` elements) and  $\mathbf{D̂_e}$ (`nd+nd*Hp` elements) as arguments. They all include the values from $k$ to $k + H_p$ (inclusively). The custom constraint also receives the slack $ϵ$ (scalar), which is always zero if `Cwt=Inf`.

    More precisely, the last two time steps in $\mathbf{U_e}$ are forced to be equal, i.e. $\mathbf{u}(k+H_p) = \mathbf{u}(k+H_p-1)$, since $H_c ≤ H_p$ implies that $\mathbf{Δu}(k+H_p) = \mathbf{0}$. The vectors $\mathbf{ŷ}(k)$ and $\mathbf{d}(k)$ are the current state estimator output and measured disturbance, respectively, and  $\mathbf{Ŷ}$ and $\mathbf{D̂}$, their respective predictions from $k+1$ to $k+H_p$.  If `LHS` represents the result of the left-hand side in the inequality  $\mathbf{g_c}(\mathbf{U_e}, \mathbf{Ŷ_e}, \mathbf{D̂_e}, \mathbf{p}, ϵ) ≤ \mathbf{0}$, the function `gc` can be implemented in two possible ways:

    1. **Non-mutating function** (out-of-place): define it as `gc(Ue, Ŷe, D̂e, p, ϵ) -> LHS`. This syntax is simple and intuitive but it allocates more memory.
    2. **Mutating function** (in-place): define it as `gc!(LHS, Ue, Ŷe, D̂e, p, ϵ) -> nothing`. This syntax reduces the allocations and potentially the computational burden as well.

    The keyword argument `nc` is the number of elements in `LHS`, and `gc!`, an alias for the `gc` argument (both `gc` and `gc!` accepts non-mutating and mutating functions). 

    By default, the optimization relies on dense [`ForwardDiff`](@extref ForwardDiff) automatic differentiation (AD) to compute the objective and constraint derivatives. One exception: if `transcription` is not a [`SingleShooting`](@ref), the `jacobian` argument defaults to this [sparse backend](@extref DifferentiationInterface AutoSparse-object):

    ```julia
    AutoSparse(
        AutoForwardDiff(); 
        sparsity_detector  = TracerSparsityDetector(), 
        coloring_algorithm = GreedyColoringAlgorithm()
    )
    ```

    Optimizers generally benefit from exact derivatives like AD. However, the [`NonLinModel`](@ref)  state-space functions must be compatible with this feature. See [`JuMP` documentation](@extref JuMP Common-mistakes-when-writing-a-user-defined-operator) for common mistakes when writing these functions.

    Note that if `Cwt≠Inf`, the attribute `nlp_scaling_max_gradient` of `Ipopt` is set to  `10/Cwt` (if not already set), to scale the small values of $ϵ$.

