```
decode(config::Sqids.Configuration, id::AbstractString)
```

Restore a numbers list from the passed `id`.

# Example

```julia-repl
julia> decode(Sqids.configure(), "86Rf07")
3-element Array{Int64,1}:
 1
 2
 3

```
