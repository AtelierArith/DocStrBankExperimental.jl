```
add_chunk!(actr::AbstractACTR; slots...)
```

Adds new chunk to declarative memory or updates existing chunk with new use. The default time is computed from `get_time`.

# Arguments

  * `actr::AbstractACTR`: an ACT-R model object

# Keywords

  * `slots...`: optional keyword arguments corresponding to slot-value pairs, e.g. name=:Bob
