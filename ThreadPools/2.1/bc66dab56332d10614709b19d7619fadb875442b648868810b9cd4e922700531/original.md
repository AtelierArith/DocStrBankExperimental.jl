```
@logbthreads -> pool
```

Mimics `Base.Threads.@threads, but keeps the iterated tasks off if the primary thread.`  Returns a logged pool that can be analyzed with the logging functions and `plot`ted.

# Example

```julia
julia> pool = @logbthreads for x in 1:8
         println((x, Threads.threadid()))
       end;
(3, 4)
(2, 3)
(1, 2)
(4, 4)
(5, 3)
(6, 2)
(8, 3)
(7, 4)

julia> plot(pool)
```

Note that execution order is not guaranteed, but the primary thread does not show up on any of the jobs.
