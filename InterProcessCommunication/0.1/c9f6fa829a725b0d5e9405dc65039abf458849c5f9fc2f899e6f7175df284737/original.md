```julia
clock_settime(id, ts)
```

set the time of the specified clock `id` to `ts`.  Argument `ts` can be an instance of `IPC.TimeSpec` or a number of seconds.  Clock identifier `id` can be `CLOCK_REALTIME` or `CLOCK_MONOTONIC` (described in [`clock_gettime`](@ref)).

See also [`clock_getres`](@ref), [`clock_gettime`](@ref), [`gettimeofday`](@ref), [`nanosleep`](@ref), [`IPC.TimeSpec`](@ref) and [`IPC.TimeVal`](@ref).
