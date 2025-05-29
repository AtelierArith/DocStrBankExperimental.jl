```
get_args(q::AbstractQuery) -> Vector{Union{String,Number}}
```

For a query object, compile all the redis arguemnts that will be used when searching in  RediSearch.

# Arguments

  * `q::AbstractQuery`: Query object.
