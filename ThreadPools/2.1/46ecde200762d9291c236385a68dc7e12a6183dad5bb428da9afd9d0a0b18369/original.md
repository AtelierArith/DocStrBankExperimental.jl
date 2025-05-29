```
logqbforeach(fn, itrs...)
```

Mimics `Base.foreach`, but launches the function evaluations onto all available  threads except the primary, using a queued scheduling strategy appropriate for  nonuniform task durations.  Returns a logged pool that can be analyzed with the  logging functions and `plot`ted.

# Example

```julia
julia> pool = logqbforeach(x -> println((x,Threads.threadid())), 1:8);
(2, 2)
(1, 3)
(3, 4)
(4, 2)
(5, 3)
(6, 4)
(7, 2)
(8, 3)

julia> plot(pool)
```

Note that the execution order is not guaranteed, and that the primary thread  is not used.
