```
Asynchronous
```

Factory object for [`LShaped.AsynchronousExecution`](@ref)/[`ProgressiveHedging.AsynchronousExecution`](@ref). Pass through the `Execution` attribute.

...

# Parameters

  * `max_active::Int = 3`: Maximum number of active iterations that run asynchronously.
  * `κ::T = 0.5`: Relative amount of finished subproblems required to start a new iterate. Governs the amount of asynchronicity.

...
