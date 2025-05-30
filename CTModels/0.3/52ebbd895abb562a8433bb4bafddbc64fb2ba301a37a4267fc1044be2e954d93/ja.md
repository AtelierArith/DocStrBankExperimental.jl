```julia
lagrange(
    ocp::CTModels.Model{<:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.AbstractControlModel, <:CTModels.AbstractVariableModel, <:Function, <:CTModels.BolzaObjectiveModel{<:Function, L<:Function}}
) -> Any

```

モデルからラグランジュコストを取得します。
