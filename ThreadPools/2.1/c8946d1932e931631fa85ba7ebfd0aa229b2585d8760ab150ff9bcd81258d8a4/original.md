```
@logqbthreads -> pool
```

Mimics `Base.Threads.@threads`, but uses a task queueing strategy, only starting a new task when an previous one (on any thread) has completed.  Returns a logged pool that can be analyzed with the logging functions and `plot`ted. The primary thread is not used.  To allow usage of the primary thread, see [`@logqthreads`](@ref).

# Example

```julia
julia> pool = @logqbthreads for x in 1:8
         println((x, Threads.threadid()))
       end;
(2, 3)
(1, 4)
(3, 2)
(4, 3)
(5, 4)
(6, 2)
(7, 3)
(8, 4)

julia> plot(pool)
```

Note that execution order is not guaranteed, but the primary thread does not show up on any of the jobs.
