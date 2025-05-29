```
respond!(actr, task, key, args...; kwargs...)
```

Executes a motor response with user defined `press_key!` function and sets module state to busy = false.

# Arguments

  * `actr`: an ACT-R model object
  * `task`: a task that is a subtype of `AbstractTask`
  * `key`: a string representing a response key
