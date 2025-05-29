```julia
trywait(sem) -> boolean
```

attempts to immediately decrement (lock) the semaphore `sem` returning `true` if successful.  If the decrement cannot be immediately performed, then the call returns `false`.  If an interruption is received or if an unexpected error occurs, an exception is thrown (`InterruptException` or `SystemError` repectively).

See also: [`Semaphore`](@ref), [`post`](@ref), [`wait`](@ref),           [`timedwait`](@ref).
