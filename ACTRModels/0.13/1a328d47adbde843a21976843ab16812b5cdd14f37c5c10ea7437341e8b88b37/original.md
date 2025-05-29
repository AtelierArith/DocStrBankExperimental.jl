```
get_chunks(memory::Vector{<:AbstractChunk}; check_value=true, criteria...)
```

Returns all chunks that matches a set criteria.

# Arguments

  * `memory::Vector{<:AbstractChunk}`: vector of chunk objects

# Keywords

  * `check_value=true`: check slot value

-`criteria...`: optional keyword arguments corresponding to critiria for matching chunk
