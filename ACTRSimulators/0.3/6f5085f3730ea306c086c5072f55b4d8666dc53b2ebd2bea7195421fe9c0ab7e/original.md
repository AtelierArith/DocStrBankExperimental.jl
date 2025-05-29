```
retrieve!(actr, chunk, args...; kwargs...)
```

Completes a memory retrieval by adding chunk to declarative memory buffer and setting busy = false and empty = false. Error is set to true if retrieval failure occurs.

# Arguments

  * `actr`: an ACT-R model object
  * `request...`: a variable list of slot-value pairs
