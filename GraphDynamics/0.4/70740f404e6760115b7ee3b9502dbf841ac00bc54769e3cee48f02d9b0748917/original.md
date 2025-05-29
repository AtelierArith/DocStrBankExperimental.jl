```
event_times(::T) = ()
```

add methods to this function if a subsystem or connection type has a discrete event that triggers at pre-defined times. This will be used to add `tstops` to the `ODEProblem` or `SDEProblem` automatically during `GraphSystem` construction. This is vital for discrete events which only trigger at a specific time.
