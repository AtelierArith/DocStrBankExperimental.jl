```
find_index(chunks::Array{<:Chunk,1}; check_value=true, criteria...)
```

Returns the index of first chunk that matches a set of criteria

# Arguments

  * `chunks`: an array of chunks

# Keywords

  * `check_value=true`:
  * `criteria`: a set of keyword arguments for slot-value pairs

# Example

```julia
chunks = [Chunk(animal=:dog), Chunk(animal=cat)]
find_index(chunks; animal=:dog)
```
