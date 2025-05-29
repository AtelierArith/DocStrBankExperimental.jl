```julia
initialize!(
    progn_new::SpeedyWeather.PrognosticVariables,
    initial_conditions::SpeedyWeather.StartFromFile,
    model::SpeedyWeather.AbstractModel
)

```

以前のSpeedyWeather.jlシミュレーションからrestart.jld2の再起動ファイルを介して再起動します。水平方向での補間は適用されますが、垂直方向では適用されません。
