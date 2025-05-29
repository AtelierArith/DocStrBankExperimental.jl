```
find_index(chunks::Array{<:Chunk,1}, funs...; check_value=true, criteria...)
```

Returns the index of first chunk that matches a set of criteria

# Arguments

  * `chunks`: an array of chunks
  * `funs`: a set of functions
  * `criteria`: a set of keyword arguments for slot-value pairs

# Keywords

  * `check_value=true`:
  * `criteria`: a set of keyword arguments for slot-value pairs

```julia
chunks = [Chunk(animal=:dog), Chunk(animal=cat)]
find_index(chunks; animal=:dog)
```
