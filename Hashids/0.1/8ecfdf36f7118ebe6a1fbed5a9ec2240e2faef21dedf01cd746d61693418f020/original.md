```
encodehex(config::Hashids.Configuration, hex::AbstractString)
```

Convert a hexadecimal string (e.g. a MongoDB id) to a hashid.

# Example

```julia-repl
julia> encodehex(Hashids.configure(), "abcdef123456")
"kmP69lB3xv"

```
