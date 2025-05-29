```julia
sigwait(mask, timeout=Inf) -> signum
```

suspends execution of the calling thread until one of the signals specified in the signal set `mask` becomes pending.  The function accepts the signal (removes it from the pending list of signals), and returns the signal number `signum`.

Optional argument `timeout` can be specified to set a limit on the time to wait for one the signals to become pending.  `timeout` can be a real number to specify a number of seconds or an instance of [`TimeSpec`](@ref).  If `timeout` is `Inf` (the default), it is assumed that there is no limit on the time to wait.  If `timeout` is a number of seconds smaller or equal zero or if `timeout` is `TimeSpec(0,0)`, the methods performs a poll and returns immediately.  It none of the signals specified in the signal set `mask` becomes pending during the allowed waiting time, a [`TimeoutError`](@ref) exception is thrown.

See also: [`sigwait!`](@ref), [`TimeSpec`](@ref), [`TimeoutError`](@ref).
