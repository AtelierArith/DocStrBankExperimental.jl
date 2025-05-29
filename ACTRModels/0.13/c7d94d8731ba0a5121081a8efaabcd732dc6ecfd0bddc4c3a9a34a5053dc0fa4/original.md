```
compute_activation!(actr::AbstractACTR, cur_time::Float64; request...)
```

Computes the activation of all chunks in declarative memory

# Arguments

  * `actr::AbstractACTR`: an `ACTR` object
  * `cur_time`: current simulated time in seconds

# Keywords

  * `request...`: optional keywords for the retrieval request
