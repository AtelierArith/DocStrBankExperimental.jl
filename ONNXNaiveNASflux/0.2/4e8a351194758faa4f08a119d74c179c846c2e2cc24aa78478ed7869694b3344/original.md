```
save(filename::AbstractString, f, args...; kwargs...)
save(io::IO, f, args...; kwargs...)
```

Serialize the result of `modelproto(f, args...; kwargs...)` to a file with path `filename` or to `io`.

See [`modelproto`](@ref) for description of arguments.
