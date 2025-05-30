```julia
final_time(
    model::CTModels.TimesModel{<:CTModels.AbstractTimeModel, CTModels.FreeTimeModel},
    variable::AbstractArray{T<:Real, 1}
) -> Any

```

自由な最終時間モデルから、時間モデルの最終時間を取得します。
