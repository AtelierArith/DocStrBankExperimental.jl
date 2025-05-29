```
Scheduler(state, T)
```

A convenience constructor of `Scheduler`

Arguments:

  * `state=EmptyState()` subtype of `AbstractState` to be used by `Scheduler`
  * `T=Float64`          type that will be used to hold time in `Scheduler`
  * `monitor=(s,Δ) -> nothing`  monitor function

By default an empty `event_queue` is created, `now` is set to `zero(T)` and there is idle `monitor`
