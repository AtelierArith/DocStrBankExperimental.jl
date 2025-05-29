```
decode(config::Hashids.Configuration, hashid::AbstractString)
```

Restore a numbers list from the passed `hashid`.

# Example

```julia-repl
julia> decode(Hashids.configure(), "o2fXhV")
3-element Array{Int64,1}:
 1
 2
 3

```
