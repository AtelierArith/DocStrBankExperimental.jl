```julia
lagrange(
    ocp::CTModels.Model{<:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.AbstractControlModel, <:CTModels.AbstractVariableModel, <:Function, CTModels.LagrangeObjectiveModel{L<:Function}}
) -> Function

```

モデルからラグランジュコストを取得します。
