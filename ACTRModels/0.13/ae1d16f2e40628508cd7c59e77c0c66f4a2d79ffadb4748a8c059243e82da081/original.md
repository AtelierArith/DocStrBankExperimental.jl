```
retrieval_prob(actr::AbstractACTR, target::Array{<:Chunk,1}, cur_time; request...)
```

Computes the retrieval probability of one chunk from a set of chunks defined in `target`. Retrieval probability is computed with the softmax approximation.

# Arguments

  * `actr::AbstractACTR`: an actr object
  * `target::Array{<:Chunk,1}`: a vector chunks in the numerator of the softmax function
  * `cur_time`: current time in seconds

# Keywords

  * `request...`: optional keywords for the retrieval request
