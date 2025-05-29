```
stan_dump(filename, data; force = false, kwargs...)
stan_dump(io, data; kwargs...)
stan_dump(StanDump.StanDumpIO(io; kwargs...), data)
```

Write `data`, which is a value that supports `pairs` (eg a `NamedTuple` or a `Dict`) to `filename` or `io`.

Using a `filename`, it will not be overwritten unless `force = true` is specified.

Keyword arguments are passed to `StanDumpIO` to govern formatting (most users should not care about this, except for debugging purposes).

# Example

```jldoctest
julia> stan_dump(stdout, (N = 1, a = 1:5, b = ones(2, 2)))
N <- 1
a <- 1:5
b <- structure(c(1.0, 1.0, 1.0, 1.0), .Dim = c(2, 2))
```
