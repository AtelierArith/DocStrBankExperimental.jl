```julia
SMCweight(
    _rng,
    algorithm,
    objective,
    proposaltune,
    cumweightsₜ₋₁
)

```

Compute cumulative and incremental weight of objective at time/iteration t, given weight at t-1. Incremental weight will be used as particle weight for resampling. Cumulative weight will be used to adapt temperature.

If temperature is constant, this function can be overloaded with your ModelName if incremental weight can be computed independent of previous weight, which speeds up computation. `cumweightsₜ` is not needed in this case.

# Examples

```julia

```
