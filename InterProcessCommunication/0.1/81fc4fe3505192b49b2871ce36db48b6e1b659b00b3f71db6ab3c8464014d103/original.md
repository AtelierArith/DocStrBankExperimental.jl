```julia
post(sem)
```

increments (unlocks) the semaphore `sem`.  If the semaphore's value consequently becomes greater than zero, then another process or thread blocked in a [`wait`](@ref) call on this semaphore will be woken up.

See also: [`Semaphore`](@ref), [`wait`](@ref), [`timedwait`](@ref),           [`trywait`](@ref).
