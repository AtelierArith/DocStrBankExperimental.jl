```julia
initial_time(
    ocp::CTModels.Model{<:CTModels.TimesModel{CTModels.FixedTimeModel{T<:Real}}}
) -> Real

```

モデルから初期時間を取得します。固定された初期時間のためです。
