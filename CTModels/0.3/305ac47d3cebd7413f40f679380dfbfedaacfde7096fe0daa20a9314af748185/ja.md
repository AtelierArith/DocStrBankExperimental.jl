```julia
variable(
    ocp::CTModels.Model{<:CTModels.TimesModel, <:CTModels.AbstractStateModel, <:CTModels.AbstractControlModel, T<:CTModels.AbstractVariableModel}
) -> CTModels.AbstractVariableModel

```

モデルから変数を取得します。
