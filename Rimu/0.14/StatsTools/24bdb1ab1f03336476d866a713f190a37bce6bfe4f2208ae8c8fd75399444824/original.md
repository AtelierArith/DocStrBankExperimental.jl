```
val(x)
```

Return the best estimate value for an uncertain `x`. Defaults to the `median` for uncertain `x` represented by a (sampled) distribution. Supports  [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl) and [`Measurements`](https://github.com/JuliaPhysics/Measurements.jl).

See [`errs`](@ref), [`BlockingResult`](@ref), [`RatioBlockingResult`](@ref).
