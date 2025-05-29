```
Dictionary{I,T}(;sizehint = 8)
```

Construct an empty hash-based dictionary. `I` and `T` default to `Any` if not specified. A `sizehint` may be specified to set the initial size of the hash table, which may speed up subsequent `insert!` operations.

# Example

```julia
julia> d = Dictionary{Int, Int}()
0-element Dictionary{Int64,Int64}
```
