```
repeat_bulk_register!(s, who, what, interval, randomize)
```

Repeat `bulk_register!` at time intervals specified by `interval` function, which must accept `Scheduler` argument. `interval` function is called after the previous event was executed. `what` must accept exactly two arguments of type `Scheduler` and `typeof(who)`. Returns `nothing`. Calling `terminate!` in function `interval` will not stop the simulation. Instead, if `interval` returns `nothing` the action is not scheduled and `repeat_register` will effectively terminate.
