```julia
make_transform(V; ...)
make_transform(V, input; kwargs...)

```

Returns a copy of `V` with transform operator (given by `transformOp(V)`) that may be applied to the provided `input` prototype array per provided keyword arguments `kwargs`.
