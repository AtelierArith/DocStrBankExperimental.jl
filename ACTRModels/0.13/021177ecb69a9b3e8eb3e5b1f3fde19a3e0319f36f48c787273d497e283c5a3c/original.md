```
retrieve(actr::AbstractACTR, cur_time; request...)
```

Retrieves a chunk given a retrieval request

# Arguments

  * `actr::AbstractACTR`: an ACT-R object
  * `cur_time`: current simulated time in seconds

# Keywords

  * `request...`: optional keyword arguments representing a retrieval request, e.g. person=:bob
