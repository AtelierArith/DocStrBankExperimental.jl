```julia
objective(
    sol::CTModels.Solution{<:CTModels.AbstractTimeGridModel, <:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.AbstractControlModel, <:CTModels.AbstractVariableModel, <:Function, O<:Real}
) -> Real

```

Return the objective value of the optimal control solution.
