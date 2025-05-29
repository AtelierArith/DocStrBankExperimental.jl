```
sim!(
    estim::StateEstimator,
    N::Int,
    u = estim.model.uop .+ 1,
    d = estim.model.dop;
    <keyword arguments>
) -> res
```

Closed-loop simulation of `estim` estimator for `N` steps, default to input bumps.

See Arguments for the available options. The noises are provided as standard deviations σ vectors. The simulated sensor and process noises of `plant` are specified by `y_noise` and `x_noise` arguments, respectively.

# Arguments

!!! info
    Keyword arguments with *`emphasis`* are non-Unicode alternatives.


  * `estim::StateEstimator` : state estimator to simulate
  * `N::Int` : simulation length in time steps
  * `u = estim.model.uop .+ 1` : manipulated input $\mathbf{u}$ value
  * `d = estim.model.dop` : plant measured disturbance $\mathbf{d}$ value
  * `plant::SimModel = estim.model` : simulated plant model
  * `u_step  = zeros(plant.nu)` : step load disturbance on plant inputs $\mathbf{u}$
  * `u_noise = zeros(plant.nu)` : gaussian load disturbance on plant inputs $\mathbf{u}$
  * `y_step  = zeros(plant.ny)` : step disturbance on plant outputs $\mathbf{y}$
  * `y_noise = zeros(plant.ny)` : additive gaussian noise on plant outputs $\mathbf{y}$
  * `d_step  = zeros(plant.nd)` : step on measured disturbances $\mathbf{d}$
  * `d_noise = zeros(plant.nd)` : additive gaussian noise on measured dist. $\mathbf{d}$
  * `x_noise = zeros(plant.nx)` : additive gaussian noise on plant states $\mathbf{x}$
  * `x_0 = plant.xop` : plant initial state $\mathbf{x}(0)$
  * `x̂_0 = nothing` or *`xhat_0`* : initial estimate $\mathbf{x̂}(0)$, [`initstate!`](@ref)  is used if `nothing`
  * `lastu = plant.uop` : last plant input $\mathbf{u}$ for $\mathbf{x̂}$ initialization

# Examples

```jldoctest
julia> model = LinModel(tf(3, [30, 1]), 0.5);

julia> estim = KalmanFilter(model, σR=[0.5], σQ=[0.25], σQint_ym=[0.01], σPint_ym_0=[0.1]);

julia> res = sim!(estim, 50, [0], y_noise=[0.5], x_noise=[0.25], x_0=[-10], x̂_0=[0, 0])
Simulation results of KalmanFilter with 50 time steps.
```
