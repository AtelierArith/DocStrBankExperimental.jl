```
reflection_coef(bc::AbstractAcousticBoundary, frequency, θ)
reflection_coef(bc::AbstractAcousticBoundary, frequency, θ, ρ, c)
```

Compute the complex reflection coefficient at a fluid-fluid boundary of type `bc` at incidence angle `θ` and `frequency`. The density and sound speed in the water are given by `ρ` and `c`, respectively.
