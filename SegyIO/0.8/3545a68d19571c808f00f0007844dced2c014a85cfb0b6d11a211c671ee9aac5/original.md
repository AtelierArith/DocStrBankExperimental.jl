```
Use: find_next_delim(x::AbstractVector, i::Int, probe_length::Int)
```

From starting index `i`, return the index of the next element in the vector that holds a different value.

# EXAMPLE

```
julia> x = vec([1 1 1 2 2 2 2 3 3 3 3]);

julia> find_next_delim(x, 1, 1)
4

julia> find_next_delim(x, 4, 1)
8
```
