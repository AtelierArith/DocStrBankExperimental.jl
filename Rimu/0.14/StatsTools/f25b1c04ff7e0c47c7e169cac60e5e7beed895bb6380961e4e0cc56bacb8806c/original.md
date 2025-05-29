```
to_measurement(p::MonteCarloMeasurements.Particles) -> ::Measurements.measurement
```

Convert an uncertain number from [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl)  to [`Measurements`](https://github.com/JuliaPhysics/Measurements.jl) format  using the median as the central point. The new `±` boundaries will include  the 68% quantile around the median.
