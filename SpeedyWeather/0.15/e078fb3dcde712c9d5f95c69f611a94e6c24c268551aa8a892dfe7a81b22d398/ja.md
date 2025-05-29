```julia
initialize!(
    model::SpeedyWeather.ShallowWater;
    time
) -> SpeedyWeather.Simulation{Model} where Model<:SpeedyWeather.ShallowWater

```

`model`のほとんどのコンポーネント（=フィールド）に対してすべての`initialize!`関数を呼び出しますが、`model.output`と`model.feedback`は常に`time_stepping!`で初期化され、`model.implicit`は`first_timesteps!`で行われます。
