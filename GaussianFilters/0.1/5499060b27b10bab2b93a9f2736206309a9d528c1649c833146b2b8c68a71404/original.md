```
simulate_step(filter::AbstractFilter, x::AbstractVector, u::AbstractVector, rng::AbstractRNG=Random.GLOBAL_RNG)
```

Run a step of simulation starting at state x, taking action u, and using the motion and measurement equations specified by the filter.
