```julia
final_time(
    ocp::CTModels.Model{<:CTModels.TimesModel{<:CTModels.AbstractTimeModel, CTModels.FreeTimeModel}},
    variable::Real
) -> Real

```

モデルから最終時間を取得します。自由な最終時間の場合です。
