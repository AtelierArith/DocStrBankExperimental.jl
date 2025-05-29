Extract list of key-value pairs from file `f`.  The result is a Vector of named tuples with two fields, `k` and `v`.

**Example**

```juliarepl
julia> kvpairs("/path/to/file.md")
3-element Vector{Any}:
 (k = "sequence", v = "16")
 (k = "hiddensequence", v = "16")
 Dict{Any, Any}()
```

```julia
kvpairs(f)

```
