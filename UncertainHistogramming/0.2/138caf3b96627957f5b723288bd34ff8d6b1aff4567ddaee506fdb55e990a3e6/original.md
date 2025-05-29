```
measurement(::ContinuousHistogram)
```

Interface to [`Measurements.jl`](https://juliaphysics.github.io/Measurements.jl/stable/).  Return a `Measurement` with `val` as the [`ContinuousHistogram`](@ref) [`mean`](@ref) and the  `err` as the [`ContinuousHistogram`](@ref) [`std`](@ref) (standard deviation).

!!! warning
    If the [`ContinuousHistogram`](@ref) in question is severely non-Gaussian, the first  two statistical [cumulants](https://en.wikipedia.org/wiki/Cumulant?oldformat=true) may be insufficient to appropriately describe the underlying distribution. In this sense,  a `measurement = value ± error` may not make sense to describe one's data.

