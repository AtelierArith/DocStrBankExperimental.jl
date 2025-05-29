```
logbforeach(fn, itrs...)
```

Mimics `Base.foreach`, but launches the function evaluations onto all available  threads except the primary, using a pre-assigned scheduling strategy appropriate  for uniform task durations.  Returns a logged pool that can be analyzed with  the logging functions and `plot`ted.    

# Example

```julia
julia> pool = logbforeach(x -> println((x,Threads.threadid())), 1:8);
(1, 2)
(3, 3)
(6, 4)
(4, 3)
(2, 2)
(7, 4)
(5, 3)
(8, 4)

julia> plot(pool)
```

Note that the execution order is not guaranteed, and that the primary thread  is not used.
