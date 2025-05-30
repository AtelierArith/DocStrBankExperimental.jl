```julia
initial_time(
    model::CTModels.TimesModel{CTModels.FreeTimeModel},
    variable::AbstractArray{T<:Real, 1}
) -> Any

```

フリー初期時間モデルから、タイムモデルの初期時間を取得します。
