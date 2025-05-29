```julia
struct NUTS{S}
```

Implementation of the “No-U-Turn Sampler” of Hoffman and Gelman (2014), including subsequent developments, as described in Betancourt (2017).

# Fields

  * `max_depth`: Maximum tree depth.
  * `min_Δ`: Threshold for negative energy relative to starting point that indicates divergence.
  * `turn_statistic_configuration`: Turn statistic configuration. Currently only `Val(:generalized)` (the default) is supported.
