```julia
gettimeofday() -> tv
```

yields the current time as an instance of `IPC.TimeVal`.  The result can be converted into a fractional number of seconds by calling `float(tv)`.

See also: [`IPC.TimeVal`](@ref), [`nanosleep`](@ref), [`clock_gettime`](@ref).
