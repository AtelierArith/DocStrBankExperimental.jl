```
retrieval_prob(actr::AbstractACTR, target::Array{<:Chunk,1}; request...)
```

Uses the softmax approximation to compute the retrieval probability of retrieving a chunk. By default, current time is computed from `get_time`.

# Arguments

  * `actr::AbstractACTR`: an ACT-R object
  * `target::Array{<:Chunk,1}`: a vector chunks in the numerator of the softmax function

# Keywords

  * `request...`: optional keyword pairs representing a retrieval request
