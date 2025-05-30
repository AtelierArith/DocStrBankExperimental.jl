```julia
control(
    sol::CTModels.Solution{<:CTModels.AbstractTimeGridModel, <:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.ControlModelSolution{TS<:Function}}
) -> Function

```

Return the control (function of time) of the optimal control solution.

```@example
julia> t0 = time_grid(sol)[1]
julia> u  = control(sol)
julia> u0 = u(t0) # control at initial time
```
