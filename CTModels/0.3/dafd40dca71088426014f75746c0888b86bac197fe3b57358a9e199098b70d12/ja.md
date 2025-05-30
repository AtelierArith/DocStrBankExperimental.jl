```julia
dynamics(
    ocp::CTModels.Model{<:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.AbstractControlModel, <:CTModels.AbstractVariableModel, D<:Function}
) -> Function

```

モデルからダイナミクスを取得します。
