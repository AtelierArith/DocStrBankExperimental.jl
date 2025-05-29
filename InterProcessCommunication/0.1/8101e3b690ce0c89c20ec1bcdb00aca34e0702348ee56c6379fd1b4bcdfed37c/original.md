```julia
clock_gettime(id) -> ts
```

yields the time of the specified clock `id`.  The result is an instance of `IPC.TimeSpec`.  Clock identifier `id` can be one of:

  * `CLOCK_REALTIME`: System-wide clock that measures real (i.e., wall-clock) time.  This clock is affected by discontinuous jumps in the system time (e.g., if the system administrator manually changes the clock), and by the incremental adjustments performed by `adjtime` and NTP.
  * `CLOCK_MONOTONIC`: Clock that cannot be set and represents monotonic time since some unspecified starting point.  This clock is not affected by discontinuous jumps in the system time.

See also [`clock_getres`](@ref), [`clock_settime`](@ref), [`gettimeofday`](@ref), [`nanosleep`](@ref), [`IPC.TimeSpec`](@ref) and [`IPC.TimeVal`](@ref).
