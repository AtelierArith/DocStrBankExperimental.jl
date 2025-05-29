```
encode(config::Hashids.Configuration, values::Array{<:Integer})  
encode(config::Hashids.Configuration, values::Integer...)
```

Encode the passed `values` to a hash.

# Example

```julia-repl
julia> encode(Hashids.configure(), 1, 2, 3)
"o2fXhV"

julia> encode(Hashids.configure(), [1, 2, 3])
"o2fXhV"

```
