```
TimePerStep(;max_steps=100)
TimePerStep(times::CircularVectorBuffer{Float64}, t::Float64)
```

Store time cost in seconds of the latest `max_steps` in the `times` field.
