```
    RealTimeCallback(interval, affect!; [offset=0.0, reset_on_freeze = false, initialize, finalize])
```

Returns a callback that executes `affect` on the [`prepropagate!`](@ref) hook every `interval` seconds system time, **starting at `offset` seconds after frst execution**. `initialize` and `finalize` functions are called when the callback is first executed and on successfull termination of the simulation respectively.

The behaviour of the timer on [`freeze!`](@ref) and subsequent [`defrost!`](@ref) is set by the `reset_on_freeze` kwarg: If set to `false` (the default option), the callback will remember how many seconds were left until the next `affect` call and resume where it left off after defrosting. If set to `true`, the timer is completely reset and will again wait for `offset` seconds after defrosting.
