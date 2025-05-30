```julia
control(
    ocp::CTModels.Model{<:CTModels.TimesModel, <:CTModels.AbstractStateModel, T<:CTModels.AbstractControlModel}
) -> CTModels.AbstractControlModel

```

モデルから制御を取得します。
