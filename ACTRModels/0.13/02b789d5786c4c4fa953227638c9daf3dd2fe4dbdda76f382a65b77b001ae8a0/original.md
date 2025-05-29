```
get_chunks(memory::Vector{<:AbstractChunk}, funs...; check_value=true, criteria...)
```

Returns all chunks that matches a set `criteria` which are evaluted according to the list of functions in `funs`.

# Arguments

  * `memory::Vector{<:AbstractChunk}`: vector of chunk objects
  * `funs...`: a list of functions

# Keywords

  * `check_value=true`: check slot value
  * `criteria...`: optional keyword arguments corresponding to critiria for matching chunk
