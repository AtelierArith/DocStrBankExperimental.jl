```julia
final_time(
    ocp::CTModels.Model{<:CTModels.TimesModel{<:CTModels.AbstractTimeModel, CTModels.FixedTimeModel{T<:Real}}}
) -> Real

```

モデルから最終時間を取得します。固定された最終時間のために。
