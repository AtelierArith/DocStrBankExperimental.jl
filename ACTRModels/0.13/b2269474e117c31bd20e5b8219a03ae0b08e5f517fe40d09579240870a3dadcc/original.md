```
find_index(actr::ACTR, funs...; check_value=true, criteria...)
```

Returns the index of first chunk that matches a set of criteria

# Arguments

  * `actr`: ACTR object
  * `funs`: a set of functions

# Keywords

  * `check_value=true`:
  * `criteria`: a set of keyword arguments for slot-value pairs

# Example

```julia
chunks = [Chunk(animal=:dog), Chunk(animal=cat)]
find_index(chunks; animal=:dog)
```
