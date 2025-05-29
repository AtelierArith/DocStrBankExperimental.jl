```julia
initialize!(
    model::SpeedyWeather.Barotropic;
    time
) -> SpeedyWeather.Simulation{Model} where Model<:SpeedyWeather.Barotropic

```

`initialize!` 関数を `model` のほとんどのフィールド、すなわちコンポーネントに対して呼び出しますが、`model.output` と `model.feedback` は常に `time_stepping!` で呼び出されます。
