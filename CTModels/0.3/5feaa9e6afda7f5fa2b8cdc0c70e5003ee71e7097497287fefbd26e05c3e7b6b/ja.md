```julia
initial_time(
    model::CTModels.TimesModel{<:CTModels.FixedTimeModel{T<:Real}}
) -> Real

```

固定初期時間モデルから、時間モデルの初期時間を取得します。
