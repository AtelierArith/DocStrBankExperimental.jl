```
logqforeach(fn, itrs...)
```

Mimics `Base.foreach`, but launches the function evaluations onto all available  threads, using a queued scheduling strategy appropriate for nonuniform task durations.

# Example

```julia
julia> pool = logqforeach(x -> println((x,Threads.threadid())), 1:8);
(2, 4)
(3, 3)
(4, 2)
(5, 4)
(6, 3)
(7, 2)
(8, 4)
(1, 1)

julia> plot(pool)
```

Note that the execution order is not guaranteed, and that the primary thread  is used.  Returns a logged pool that can be analyzed with the logging functions  and `plot`ted.
