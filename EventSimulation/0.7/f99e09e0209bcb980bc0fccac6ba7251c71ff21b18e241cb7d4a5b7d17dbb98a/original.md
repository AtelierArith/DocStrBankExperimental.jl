```
bulk_register!(s, who, what, Δ, randomize)
```

Put event at time `s.now+Δ` to `s.event_queue` that will execute `what(scheduler, w)` for all `w` in `who`. If `randomize` is `false` then `who` is traversed in natural order otherwise it is traversed in random order. `what` must accept exactly two arguments of type `Scheduler` and `eltype(who)`. The function does not check if `Δ` is a valid (finite) number. Returns inserted bulk `Action`.

Function is designed to efficiently handle case when the same action has to be executed at the same simulation time by many agents.
