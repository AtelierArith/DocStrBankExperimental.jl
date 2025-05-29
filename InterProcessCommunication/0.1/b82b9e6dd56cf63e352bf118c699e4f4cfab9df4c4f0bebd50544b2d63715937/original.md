```julia
nanosleep(t) -> rem
```

sleeps for `t` seconds with nanosecond precision and returns the remaining time (in case of interrupts) as an instance of `IPC.TimeSpec`.  Argument can be a (fractional) number of seconds or an instance of `IPC.TimeSpec` or `IPC.TimeVal`.

The `sleep` method provided by Julia has only millisecond precision.

See also [`gettimeofday`](@ref), [`IPC.TimeSpec`](@ref) and [`IPC.TimeVal`](@ref).
