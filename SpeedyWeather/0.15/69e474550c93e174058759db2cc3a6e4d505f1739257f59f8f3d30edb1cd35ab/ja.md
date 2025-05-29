```julia
tree(
    S::SpeedyWeather.Simulation{M};
    modules,
    with_size,
    kwargs...
)

```

Simulationインスタンス内のフィールドのツリーを作成し、modules引数内で定義されている限り、これらのフィールド内のフィールドを作成します（デフォルトはSpeedyWeather）。他のキーワード引数は`max_level::Integer=10`、`with_types::Bool=false`または`with_size::Bool=false`です。
