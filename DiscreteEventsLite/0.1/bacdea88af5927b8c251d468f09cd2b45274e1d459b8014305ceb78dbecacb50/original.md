```
register!(scheduler, fun, when, t, args...; id="", description="", kwargs...)
```

An interface for adding events to the scheduler. 

# Arguments

  * `scheduler`: an event scheduler
  * `fun`: a function to execute
  * `when`: timing for the execution of `fun`. Options: `at`, `now`, `every`, `after`
  * `t`: time value associated with `when`
  * `args...`: optional positional arguments for `fun`
  * `id`: optional id string
  * `description`: optional description

# Keywords

  * `kwargs...`: option keyword arguments for `fun`
