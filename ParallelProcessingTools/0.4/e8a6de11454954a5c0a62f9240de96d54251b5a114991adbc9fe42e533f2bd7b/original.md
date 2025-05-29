```
wait_for_any(
    objs...;
    maxtime::Union{Real,Nothing} = nothing, timeout_error::Bool = false
)

wait_for_all(objs::Union{Tuple,AbstractVector,Base.Generator,Base.ValueIterator}; kwargs...)
```

Wait for any of the objects `objs` to become ready.

Readiness of objects is as defined by [`wouldwait`](@ref). Objects that are `Nothing` are ignored, i.e. not waited for.

See [`@wait_while`](@ref) for the effects of `maxtime` and `timeout_error`.

Example, wait for a task with a timeout:

```julia
task1 = Threads.@spawn sleep(1.0)
task2 = Threads.@spawn sleep(5.0)
wait_for_any(task1, task2, maxtime = 3.0)
istaskdone(task1) == true
istaskdone(task2) == false
```

Similar to `waitany` (new in Julia v1.12), but applies to a wider range of object types.
