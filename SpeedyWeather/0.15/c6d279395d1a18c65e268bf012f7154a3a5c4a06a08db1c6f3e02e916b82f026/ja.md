```julia
initialize!(
    model::SpeedyWeather.PrimitiveWet;
    time
) -> SpeedyWeather.Simulation{Model} where Model<:SpeedyWeather.PrimitiveWet

```

`model`のコンポーネントのすべての`initialize!`関数を呼び出しますが、`model.output`と`model.feedback`は常に`time_stepping!`で呼び出され、`model.implicit`は`first_timesteps!`で行われます。
