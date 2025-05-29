```
register!(s, what, Δ)
```

Put `what` at time `s.now+Δ` to `s.event_queue`. `what` must accept exactly one argument of type `Scheduler`. The function does not check if `Δ` is a valid (finite) number. Returns inserted `Action`.
