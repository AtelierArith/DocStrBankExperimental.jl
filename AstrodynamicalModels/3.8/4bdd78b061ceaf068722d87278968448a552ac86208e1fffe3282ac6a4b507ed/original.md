```julia
PlanarEntrySystem(; name, defaults, kwargs...)

```

A `ModelingToolkit.ODESystem` for atmospheric entry. Currently, only exponential atmosphere models are provided! The output model is cached with `Memoize.jl`. Planet-specific parameters default to Earth values.

The order of the states follows: `[γ, v, r, θ]`.

The order of the parameters follows: `[R, P, H, m, A, C, μ]`

# Extended Help

This model describes how an object moves through an exponential atmosphere, above a spherical planet.

### Usage

```julia
model = PlanarEntrySystem()
```
