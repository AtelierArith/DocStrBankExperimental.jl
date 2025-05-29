Find list of key-value pairs for a given note in a vault. The result is a Vector of named tuples with fields `k` and `v`.

**Example**

```juliarepl
julia> kvpairs(v, notenames[1])
3-element Vector{Any}:
 (k = "sequence", v = "16")
 (k = "hiddensequence", v = "16")
 Dict{Any, Any}()
```

```julia
kvpairs(v, note)

```
