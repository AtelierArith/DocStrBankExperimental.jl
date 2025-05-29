```
Clock <: AbstractClock
Clock([t]; dt)
```

The default periodic clock with independent variables `t` and tick interval `dt`. If `dt` is left unspecified, it will be inferred (if possible).
