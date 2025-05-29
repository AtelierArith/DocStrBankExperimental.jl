```
first_chunk(memory::Vector{<:Chunk}; check_value=true, criteria...)
```

Returns the first chunk in memory that matches a set of criteria

# Arguments

  * `memory::Vector{<:Chunk}`: a vector of chunks

# Keywords

  * `check_value=true`: check slot value
  * `criteria...`: optional keyword arguments corresponding to critiria for matching chunk
