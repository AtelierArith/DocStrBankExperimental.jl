```
decodehex(config::Hashids.Configuration, hashid::AbstractString)
```

Resrtore a hexadecimal string (e.g. a MongoDB id) from the passed `hashid`.

# Example

```julia-repl
julia> decodehex(Hashids.configure(), "kmP69lB3xv")
"abcdef123456"

```
