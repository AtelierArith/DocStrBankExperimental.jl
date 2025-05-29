```
compute_activation!(actr::AbstractACTR, chunks::Vector{<:Chunk}; request...)
```

Computes the activation of a vector of chunks. By default, current time is computed with `get_time`.

# Arguments

  * `actr::AbstractACTR`: an `ACTR` object
  * `chunks::Vector{<:Chunk}`: a vector of chunks.

# Keywords

  * `request...`: optional keywords for the retrieval request
