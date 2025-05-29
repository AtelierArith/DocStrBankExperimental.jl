```
sim!(
    mpc::PredictiveController, 
    N::Int,
    ry = mpc.estim.model.yop .+ 1, 
    d  = mpc.estim.model.dop,
    ru = mpc.estim.model.uop;
    <keyword arguments>
) -> res
```

Closed-loop simulation of `mpc` controller for `N` steps, default to output setpoint bumps.

The output and manipulated input setpoints are held constant at `ry` and `ru`, respectively. The keyword arguments are identical to [`sim!(::StateEstimator, ::Int)`](@ref).

# Examples

```jldoctest
julia> model = LinModel([tf(3, [30, 1]); tf(2, [5, 1])], 4);

julia> mpc = setconstraint!(LinMPC(model, Mwt=[0, 1], Nwt=[0.01], Hp=30), ymin=[0, -Inf]);

julia> res = sim!(mpc, 25, [0, 0], y_noise=[0.1], y_step=[-10, 0])
Simulation results of LinMPC with 25 time steps.
```
