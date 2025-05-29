```
BurstModeCallback(; interval, affect, maxcount=10, trigger_offset=0.0, trigger_interval=10.0) <: AbstractCallback
```

Returns a callback that executes `affect` every interval time units for a total of `maxcount` iterations after it has been triggered by a `PeriodicCallback` that is initialized with `trigger_offset` and `trigger_interval`.

## Example

A callback created with

```
BurstModeCallback(; interval=0.1,
                        affect=printcurrenttime,
                        maxcount=3,)
```

where `printcurrenttime` does what you think it does, will, during a simulation, print `0.0, 0.1, 0.2, 10.0, 10.1, 10.2, 20.0, ...`
