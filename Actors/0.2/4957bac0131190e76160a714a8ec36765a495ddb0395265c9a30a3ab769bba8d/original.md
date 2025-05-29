```
monitor(lk::Link, onsignal...)
monitor(t::Task, onsignal...; timeout::Real=5.0, pollint::Real=0.1)
```

Start monitoring the actor represented by `lk` or the task `t` and execute `onsignal...` if it sends [`Down`](@ref) or if it fails.

# Parameters

  * `onsignal...`: action to take on `Down` signal: 

      * if empty, it gives a warning;
      * if it is one argument `f`, it executes with  `f(msg.reason)`;
      * if `f, args...`, it gets executed with  `f(args..., msg.reason)`.
  * `timeout::Real=5.0`: how many seconds should a task    be monitored? After that a [`Down`](@ref) with   reason `:timed_out` is sent.
  * `pollint::Real=0.1`: polling interval in seconds for   task monitoring.
