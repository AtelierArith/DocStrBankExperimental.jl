```
mutable struct Clock{T, FT}
```

Keeps track of the current `time`, `last_Δt`, `iteration` number, and time-stepping `stage`. The `stage` is updated only for multi-stage time-stepping methods. The `time::T` is either a number or a `DateTime` object.
