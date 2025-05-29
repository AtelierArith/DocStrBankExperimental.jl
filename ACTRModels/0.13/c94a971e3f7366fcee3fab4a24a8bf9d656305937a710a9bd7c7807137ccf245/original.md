```
compute_activation!(actr::AbstractACTR, chunks::Vector{<:Chunk}, cur_time::Float64; request...)
```

Computes the activation of a vector of chunks

# Arguments

  * `actr::AbstractACTR`: an `ACTR` object
  * `chunks::Vector{<:Chunk}`: a vector of chunks.
  * `cur_time::Float64`: current simulated time in seconds

# Keywords

  * `request...`: optional keywords for the retrieval request
