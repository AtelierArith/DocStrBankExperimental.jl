```
wait_for_all(
    objs...;
    maxtime::Union{Real,Nothing} = nothing, timeout_error::Bool = false
)

wait_for_all(objs::Union{Tuple,AbstractVector,Base.Generator,Base.ValueIterator}; kwargs...)
```

Wait for all of the `objs` to become ready.

Readiness of objects is as defined by [`wouldwait`](@ref). Objects that are `Nothing` are ignored, i.e. not waited for.

See [`@wait_while`](@ref) for the effects of `maxtime` and `timeout_error`.

Example, wait for two tasks to finish:

```julia
task1 = Threads.@spawn sleep(10)
task2 = Threads.@spawn sleep(2)
wait_for_all(task1, task2)
```
