```
RunTillLastStep(step::Int = 0 # number of current/starting timestep
             laststep::Int = 100 # number of final timestep
             shiftMode::Bool = false # whether to adjust shift
             shift = 0.0 # starting/current value of shift
             dτ::Float64 = 0.01 # current value of time step
) <: FciqmcRunStrategy
```

Parameters for running [`lomc!()`](@ref) for a fixed number of time steps. For alternative strategies, see [`FciqmcRunStrategy`](@ref).

!!! warning
    The use of this strategy is deprecated. Pass the relevant arguments directly to [`ProjectorMonteCarloProblem`](@ref) or to [`lomc!()`](@ref) instead.

