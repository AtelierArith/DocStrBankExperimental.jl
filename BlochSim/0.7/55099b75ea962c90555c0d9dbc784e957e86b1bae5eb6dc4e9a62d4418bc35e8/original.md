```
GradientSpoiling(grad, Tg) <: AbstractSpoiling
GradientSpoiling(gx, gy, gz, Tg)
```

Represents gradient spoiling, e.g., applying a gradient `grad = Gradient(gx, gy, gz)` for time `Tg` (ms). `grad` can be a `Gradient` (or `gx`, `gy`, and `gz` can be scalars), representing a constant gradient, or `grad` can be a collection of `Gradient`s (or `gx`, `gy`, and `gz` can be collections of values), representing a gradient waveform with a constant time step.
