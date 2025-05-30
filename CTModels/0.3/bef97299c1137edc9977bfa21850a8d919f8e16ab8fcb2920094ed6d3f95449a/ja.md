```julia
initial_time(
    ocp::CTModels.Model{<:CTModels.TimesModel{CTModels.FreeTimeModel}},
    variable::Real
) -> Real

```

モデルから初期時間を取得します。自由な初期時間の場合です。
