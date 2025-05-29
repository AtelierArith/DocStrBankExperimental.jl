```
attend!(actr, chunk, args...; kwargs...)
```

Completes an attention shift by adding a `chunk` to the visual buffer and setting states to busy = false and empty = false.

# Arguments

  * `actr`: an ACT-R model object
  * `chunk`: a memory chunk
