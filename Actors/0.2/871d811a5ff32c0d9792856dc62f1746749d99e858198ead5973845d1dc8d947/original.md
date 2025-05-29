```
start_task(start, sv, cb=nothing; 
           timeout::Real=5.0, pollint::Real=0.1)
```

Spawn a task with a `start` behavior and tell the supervisor `sv` to supervise it (with restart strategy `:transient`) and return a reference to it.

# Parameters

  * `start`: must be a callable object (with no arguments),
  * `sv`: link or registered name of a supervisor,
  * `cb=nothing`: callback for restart (a callable object, must    return a `Task`); if `cb=nothing`, the task gets restarted    with its `start` function,
  * `timeout::Real=5.0`: how long [seconds] should the task    be supervised,
  * `pollint::Real=0.1`: polling interval [seconds].
