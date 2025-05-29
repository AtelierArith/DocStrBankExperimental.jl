```
mix(x::AbstractSampler, y::AbstractSampler, t::Real)
```

Construct a modifier sampler that outputs the result of linearly interpolating the output of samplers `x` and `y` by the scalar `t`.
