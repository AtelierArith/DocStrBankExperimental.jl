```
responding!(actr, task, key, args...; kwargs...)
```

Sets the declarative motor module as busy and registers a new event for executing a key stroke

# Arguments

  * `actr`: an ACT-R model object
  * `task`: a task that is a subtype of `AbstractTask`
  * `key`: a string representing a response key
