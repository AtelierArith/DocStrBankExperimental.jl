```
qforeach(fn, itrs...)
```

Mimics `Base.foreach`, but launches the function evaluations onto all available  threads, using a queued scheduling strategy appropriate for nonuniform task durations.

# Example

```julia
julia> qforeach(x -> println((x,Threads.threadid())), 1:8)
(4, 3)
(2, 2)
(3, 4)
(5, 3)
(6, 2)
(7, 4)
(8, 3)
(1, 1)
```

Note that the execution order is not guaranteed, and that the primary thread  is used.
