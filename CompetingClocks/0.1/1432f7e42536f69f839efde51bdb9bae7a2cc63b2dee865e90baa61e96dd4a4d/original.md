```
next(dc::DirectCall, when::TimeType, rng::AbstractRNG)
```

Ask the sampler what clock will be the next to fire and at what time. This does not change the sampler. You can call this multiple times and get multiple answers. Each answer is a tuple of `(when, which clock)`. If there is no clock to fire, then the response will be `(Inf, nothing)`. That's a good sign the simulation is done.
