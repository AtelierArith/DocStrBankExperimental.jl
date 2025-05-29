```
retrieval_prob(actr::AbstractACTR, chunk::AbstractChunk, cur_time=0.0; request...)
```

Uses the softmax approximation to compute the retrieval probability of retrieving a chunk.

# Arguments

  * `actr::AbstractACTR`: an ACT-R object
  * `chunk::AbstractChunk`: a chunk
  * `cur_time`: current simulated time in seconds

# Keywords

  * `request...`: optional keyword pairs representing a retrieval request
