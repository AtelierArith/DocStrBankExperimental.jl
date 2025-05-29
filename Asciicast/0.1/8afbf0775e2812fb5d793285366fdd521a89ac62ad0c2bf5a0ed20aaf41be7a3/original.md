```
record_output(f, filepath::AbstractString, start_time::Float64=time(); delay=0, kw...) -> filepath
record_output(f, io::IO=IOBuffer(), start_time::Float64=time(); delay=0, kw...)
```

Executes `f()` while saving all output to a cast whose data is saved to `io`, or to a file at `filepath`. The arguments `kw...` may be any keyword arguments accepted by [`Header`](@ref).

The parameters of the cast may be passed here; see [`Cast`](@ref) for more details.

Returns a `Cast` object.
