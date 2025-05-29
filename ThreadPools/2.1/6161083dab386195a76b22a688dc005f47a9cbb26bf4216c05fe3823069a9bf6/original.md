```
@logthreads -> pool
```

Mimics `Base.Threads.@threads`.  Returns a logged pool that can be analyzed with the logging functions and `plot`ted.

# Example

```julia
julia> pool = @logthreads for x in 1:8
         println((x, Threads.threadid()))
       end;
(1, 1)
(5, 3)
(7, 4)
(2, 1)
(6, 3)
(8, 4)
(3, 2)
(4, 2)

julia> plot(pool)
```

Note that execution order is not guaranteed and the primary thread is used.
