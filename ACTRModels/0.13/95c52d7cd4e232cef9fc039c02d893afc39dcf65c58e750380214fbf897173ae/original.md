```
add_chunk!(actr::AbstractACTR, cur_time=0.0; slots...)
```

Adds new chunk to declarative memory or updates existing chunk with new use

# Arguments

  * `actr::AbstractACTR`: an ACT-R model object
  * `cur_time=0.0`: current simulated time in seconds

# Keywords

  * `slots...`: optional keyword arguments corresponding to slot-value pairs, e.g. name=:Bob
