```julia
objective(
    ocp::CTModels.Model{<:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.AbstractControlModel, <:CTModels.AbstractVariableModel, <:Function, O<:CTModels.AbstractObjectiveModel}
) -> CTModels.AbstractObjectiveModel

```

モデルから目的関数を取得します。
