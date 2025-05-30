```julia
dynamics(
    ocp::CTModels.Model{<:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.AbstractControlModel, <:CTModels.AbstractVariableModel, D<:Function}
) -> Function

```

Get the dynamics from the model.
