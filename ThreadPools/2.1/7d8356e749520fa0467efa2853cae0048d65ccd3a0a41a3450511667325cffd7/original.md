```
@logqthreads -> pool
```

Mimics `Base.Threads.@threads`, but uses a task queueing strategy, only starting a new task when an previous one (on any thread) has completed.  Returns a logged pool that can be analyzed with the logging functions and `plot`ted. The primary thread is used.  To prevent usage of the primary thread, see [`@logqbthreads`](@ref).

# Example

```julia
julia> pool = @logqthreads for x in 1:8
         println((x, Threads.threadid()))
       end;
(1, 1)
(3, 2)
(7, 4)
(5, 3)
(2, 1)
(8, 4)
(6, 3)
(4, 2)

julia> plot(pool)
```

Note that execution order is not guaranteed and the primary thread is used.
