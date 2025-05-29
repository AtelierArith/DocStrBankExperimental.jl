```
@qbthreads
```

Mimics `Base.Threads.@threads`, but uses a task queueing strategy, only starting a new task when an previous one (on any thread) has completed.  This can provide performance advantages when the iterated tasks are very nonuniform in length. The primary thread is not used.  To allow usage of the primary thread, see [`@qthreads`](@ref).

# Example

```julia
julia> @qbthreads for x in 1:8
         println((x, Threads.threadid()))
       end
(2, 4)
(3, 2)
(1, 3)
(4, 4)
(5, 2)
(6, 3)
(7, 4)
(8, 2)
```

Note that execution order is not guaranteed, but the primary thread does not show up on any of the jobs.
