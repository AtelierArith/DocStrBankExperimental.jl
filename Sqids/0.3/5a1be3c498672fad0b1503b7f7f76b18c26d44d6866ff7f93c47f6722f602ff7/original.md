```
encode(config::Sqids.Configuration, numbers::Array{<:Integer})
```

Encode the passed `numbers` to an id.

# Example

```julia-repl
julia> encode(Sqids.configure(), [1, 2, 3])
"86Rf07"

```
