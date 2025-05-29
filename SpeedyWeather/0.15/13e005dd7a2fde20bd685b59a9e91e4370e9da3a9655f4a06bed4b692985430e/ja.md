```julia
initialize!(
    output::SpeedyWeather.JLD2Output,
    feedback::SpeedyWeather.AbstractFeedback,
    progn::SpeedyWeather.PrognosticVariables,
    diagn::SpeedyWeather.DiagnosticVariables,
    model::SpeedyWeather.AbstractModel
)

```

JLD2 `output`を初期化するには、JLD2ファイルを作成します。最初のタイムステップの直前に呼び出されます。
