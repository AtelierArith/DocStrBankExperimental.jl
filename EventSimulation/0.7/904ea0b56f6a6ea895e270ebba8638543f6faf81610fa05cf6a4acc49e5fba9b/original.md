```
repeat_register!(s, what, interval)
```

Put `what` to `s.event_queue` repeatedly in time intervals specified by `interval` function, which must accept one argument of type `Scheduler`. `what` must accept exactly one argument of type `Scheduler`. `interval` function is called after the previous event was executed. Returns `nothing`. Calling `terminate!` in function `interval` will not stop the simulation. Instead, if `interval` returns `nothing` the action is not scheduled and `repeat_register` will effectively terminate.
