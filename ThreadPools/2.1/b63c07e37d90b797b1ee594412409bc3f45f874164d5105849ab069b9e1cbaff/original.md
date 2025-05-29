```
@qthreads
```

Mimics `Base.Threads.@threads`, but uses a task queueing strategy, only starting a new task when an previous one (on any thread) has completed.  This can provide performance advantages when the iterated tasks are very nonuniform in length. The primary thread is used.  To prevent usage of the primary thread, see [`@qbthreads`](@ref).

# Example

```julia
julia> @qthreads for x in 1:8
         println((x, Threads.threadid()))
       end
(2, 4)
(3, 3)
(4, 2)
(5, 4)
(6, 3)
(7, 2)
(8, 4)
(1, 1)
```

Note that execution order is not guaranteed and the primary thread is used.
