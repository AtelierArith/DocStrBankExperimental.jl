```
PeriodicCallback(affect, interval; [offset=0.0, initialize, finalize])
```

Returns a callback that executes `affect` on the [`prepropagate!`](@ref) hook every `interval` simulation time units, **starting at `offset + interval`**. `initialize` and `finalize` functions are called when the callback is first executed and on successfull termination of the simulation respectively.
