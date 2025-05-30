```julia
costate(
    sol::CTModels.Solution{<:CTModels.AbstractTimeGridModel, <:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.AbstractControlModel, <:CTModels.AbstractVariableModel, Co<:Function}
) -> Function

```

Return the costate of the optimal control solution.

```@example
julia> t0 = time_grid(sol)[1]
julia> p  = costate(sol)
julia> p0 = p(t0)
```
