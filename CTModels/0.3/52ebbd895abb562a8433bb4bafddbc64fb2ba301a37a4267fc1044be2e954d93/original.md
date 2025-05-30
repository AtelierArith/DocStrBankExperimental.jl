```julia
lagrange(
    ocp::CTModels.Model{<:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.AbstractControlModel, <:CTModels.AbstractVariableModel, <:Function, <:CTModels.BolzaObjectiveModel{<:Function, L<:Function}}
) -> Any

```

Get the Lagrange cost from the model.
