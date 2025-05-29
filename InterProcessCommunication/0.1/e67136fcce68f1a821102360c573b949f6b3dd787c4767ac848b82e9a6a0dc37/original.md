```julia
timedlock(rwlock, mode, lim) -> bool
```

locks read/write lock object `rwlock` for reading if `mode` is `'r'`, for writing if `mode` is `'w'`, but waits no longer than the time limit specified by `lim`.  The returned boolean value indicates whether the object could be locked before the time limit.

Argument `lim` can be and instance of [``TimeSpec`](@ref) or [`TimeVal`](@ref) to specify an absolute time limit since the Epoch, or a real to specify a limit as a number of seconds relative to the current time.

See Also: [`trylock`](@ref).
