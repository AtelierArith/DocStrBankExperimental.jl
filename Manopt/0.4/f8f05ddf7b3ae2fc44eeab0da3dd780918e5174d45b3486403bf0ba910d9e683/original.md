```
RecordTime <: RecordAction
```

record the time elapsed during the current iteration.

The three possible modes are

  * `:cumulative` record times without resetting the timer
  * `:iterative` record times with resetting the timer
  * `:total` record a time only at the end of an algorithm (see [`stop_solver!`](@ref))

The default is `:cumulative`, and any non-listed symbol default to using this mode.

# Constructor

```
RecordTime(; mode::Symbol=:cumulative)
```
