```
select(x::AbstractSampler, y::AbstractSampler; kwargs...)
```

Construct a modifier sampler that outputs either the out of sampler `x` or `y`, depending on the output of sampler `z`.

If the output of sampler `z` is within the range denoted by `min` and `max`, the output of sampler `y` is chosen. If the output of sampler `z` is outside of this range, the output of sampler `x` is chosen.

# Arguments

  * `min`: A real number between -1.0 and 1.0 defining the lower bound of the selection range.
  * `max`: A real number between -1.0 and 1.0 defining the upper bound of the selection range.
  * `falloff`: A real number between 0.0 and 1.0 specifying the smoothness of the transition.
