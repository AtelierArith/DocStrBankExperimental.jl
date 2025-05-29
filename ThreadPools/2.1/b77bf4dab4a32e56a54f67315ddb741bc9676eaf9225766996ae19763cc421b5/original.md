```
logtforeach(fn, itrs...) -> pool
```

Mimics `Base.foreach`, but launches the function evaluations onto all available  threads, using a pre-assigned scheduling strategy appropriate for uniform task durations.  Returns a logged pool that can be analyzed with  the logging functions and `plot`ted.

# Example

```julia
julia> pool = logtforeach(x -> println((x,Threads.threadid())), 1:8);
(1, 1)
(3, 2)
(7, 4)
(2, 1)
(4, 2)
(5, 3)
(8, 4)
(6, 3)

julia> plot(pool)
```

Note that the execution order is not guaranteed, and that the primary thread  is used.
