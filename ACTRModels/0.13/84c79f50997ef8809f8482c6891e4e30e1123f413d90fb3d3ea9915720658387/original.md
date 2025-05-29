```
retrieval_prob(actr::AbstractACTR, chunk::AbstractChunk; request...)
```

Uses the softmax approximation to compute the retrieval probability of retrieving a chunk. By default, current time is computed from `get_time`.

# Arguments

  * `actr::AbstractACTR`: an ACT-R object
  * `chunk::AbstractChunk`: a chunk

# Keywords

  * `request...`: optional keyword pairs representing a retrieval request
