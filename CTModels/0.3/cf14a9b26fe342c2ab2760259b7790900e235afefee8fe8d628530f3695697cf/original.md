```julia
state(
    sol::CTModels.Solution{<:CTModels.AbstractTimeGridModel, <:CTModels.AbstractTimesModel, <:CTModels.StateModelSolution{TS<:Function}}
) -> Function

```

Return the state (function of time) of the optimal control solution.

```@example
julia> t0 = time_grid(sol)[1]
julia> x  = state(sol)
julia> x0 = x(t0)
```
