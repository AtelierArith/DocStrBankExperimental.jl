```julia
clock_getres(id) -> ts
```

yields the resolution (precision) of the specified clock `id`. The result is an instance of `IPC.TimeSpec`.  Clock identifier `id` can be `CLOCK_REALTIME` or `CLOCK_MONOTONIC` (described in [`clock_gettime`](@ref)).

See also [`clock_gettime`](@ref), [`clock_settime`](@ref), [`gettimeofday`](@ref), [`nanosleep`](@ref), [`IPC.TimeSpec`](@ref) and [`IPC.TimeVal`](@ref).
