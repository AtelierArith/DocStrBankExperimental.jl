```
retrieval_probs(actr::AbstractACTR, cur_time; request...)
```

Computes the retrieval probability for each chunk matching the retrieval request.

# Arguments

  * `actr::AbstractACTR`: an actr object
  * `cur_time`: current simulated time in seconds

# Keywords

  * `request...`: optional keyword pairs representing a retrieval request
