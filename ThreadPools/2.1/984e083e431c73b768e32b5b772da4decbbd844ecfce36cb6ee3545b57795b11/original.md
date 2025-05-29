```
qbforeach(fn, itrs...)
```

Mimics `Base.foreach`, but launches the function evaluations onto all available  threads except the primary, using a queued scheduling strategy appropriate for  nonuniform task durations.

# Example

```julia
julia> qbforeach(x -> println((x,Threads.threadid())), 1:8)
(3, 3)
(2, 4)
(1, 2)
(4, 3)
(5, 4)
(6, 2)
(7, 3)
(8, 4)
```

Note that the execution order is not guaranteed, and that the primary thread  is not used.
