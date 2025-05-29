```
mix(x::AbstractSampler, y::AbstractSampler, t::AbstractSampler)
```

Construct a modifier sampler that outputs the result of linearly interpolating the output of samplers `x` and `y` by the output of sampler `t`.
