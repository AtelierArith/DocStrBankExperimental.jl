```
to_measurement(p::MonteCarloMeasurements.Particles) -> ::Measurements.measurement
```

不確実な数値を [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl) から [`Measurements`](https://github.com/JuliaPhysics/Measurements.jl) 形式に変換します。中央値を中心点として使用します。新しい `±` 境界は中央値の周りの68%分位点を含みます。
