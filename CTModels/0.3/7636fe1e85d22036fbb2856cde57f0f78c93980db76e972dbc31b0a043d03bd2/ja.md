```julia
final_time(
    model::CTModels.TimesModel{<:CTModels.AbstractTimeModel, <:CTModels.FixedTimeModel{T<:Real}}
) -> Real

```

固定された最終時間モデルから、時間モデルの最終時間を取得します。
